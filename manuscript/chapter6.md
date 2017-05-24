# ¿Por qué PowerShell Remoting? (Mientras respondemos otros "por qué"…)

Una pregunta común es, "¿por qué deberíamos habilitar PowerShell Remoting?"

Antes de responder hay que entender un par de cosas - va a parecer un poco grosero. Lo siento.

- PowerShell Remoting ha existido desde 2008. Si usted se está preguntando esto hasta ahora, entonces usted está haciendo un trabajo “modesto” en la gestión de su entorno. En 2008 también aparecieron los relojes inteligentes, Microsoft (antes Windows) Azure, el Roadster de Tesla, "Frozen" de Disney, las bombillas led con precios razonables, y los modelos de iPhone 3G, 3GS, 4, 4S, 5, 5S, y 6. Sólo en caso de que se los haya perdido también.

- Las tecnologías de la información son una industria en constante cambio. Las decisiones perfectamente razonables que tomó en 2003 van a necesitar ser revisadas periódicamente, debido al cambio mencionado anteriormente.

Una vez aclarado esto, vamos a hablar brevemente de ...

## ¿Qué es PowerShell Remoting?

Remoting es simplemente una manera en que las herramientas de administración en una computadora se hablan con servicios en otra computadora, de modo que pueda administrar remotamente esos servicios.

Remoting se basa en http, y utiliza un protocolo llamado WS-Management (WS-MAN). Requiere que los servidores tengan un único puerto abierto para enrutar todo el tráfico de gestión entrante a través de ese puerto. El tráfico de WS-MAN puede ser registrado, puede ser enviado a través de un Proxy, a través de servidores de seguridad (proporcionados por terceros), y puede ser completamente cifrado por medio de SSL.

Como todo el tráfico es http, Remoting es esencialmente un transmisor de texto de ida y vuelta. Remoting simplemente especifica la forma de intercambiar un texto (generalmente una variante de XML) para que las herramientas y servicios puedan entenderse mutuamente.

El control remoto no afecta en modo alguno la seguridad de la red ni las configuraciones predeterminadas. Por defecto, no se transmiten nombres de usuario o contraseñas, estén cifrados o no. En un entorno que no sea de dominio, puede crear una variante en el que se transmitirán contraseñas, pero si usted quisiera cifrarlas por SSL, puede utilizar https.

Remoting no le otorga a nadie privilegios especiales. La tecnología literalmente no permite que alguien haga algo que no tiene permiso para hacer, a menos que haya pasado por una configuración bastante compleja conocida como administración delegada. En ese caso, puede habilitar a usuarios específicos para realizar tareas específicas que normalmente no podrían hacerlo, pero sólo a través del canal específico y la interfaz que ha configurado.

## Comparing Remoting to what came before
Before Remoting, most Windows remote management was conducted over Remote Procedure Calls, or RPCs. These usually employed port-hopping, making them incredibly difficult to manage through a firewall. Contrast that with the one port you have to deal with in Remoting.

A lot of organizations today simply install management tools on servers, and then use Remote Desktop to "remotely manage." That's an incredibly poor idea, and is a major reason why Windows Server take so many patches, so many reboots, and other maladies. The code needed to support a full GUI, and therefore RDP, is massive - and that means patches are inevitable. Running management tools _on the server_, usually under administrator credentials, is opening the door to an attack.

In short, most organizations seem to be worred about the security "implications" of PowerShell Remoting. The implications are **significant** - Remoting is **much** more secure than what you've been doing. It's also more efficient, imposes less overhead on servers, and lets servers run with a leaner operating system that will require fewer patches, fewer reboots, and fewer service packs. Those servers will also boot faster, run fewer processes, run fewer services, and consume less storage space for the OS. Those servers will require less memory overhead for the OS, meaning you can pack more of 'em into a virtualization host. Sounds horrible, right?

## But here's the best reason
Quite simply, the main reason to enable Remoting is that _you haven't got any choice._ Microsoft has moved firmly in this direction, and enables Remoting by default on Windows Server 2012 and later. The company _disables_ Remote Desktop by default, which should tell you something. 

Further, in Nano Server, _logging onto the console isn't even an option_, whether you use Remote Desktop or not. There _is_ no local login. Remoting _is literally your only option_ for managing the server. That's going to be the case going forward.

Running a Windows environment without enabling Remoting - at least on servers - is like driving a car without wanting to depress the accelerator. It isn't much fun, and you aren't going to get very far.
