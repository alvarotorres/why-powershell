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

## Comparando Remoting con sus antecesores

Antes de Remoting, la mayoría de la administración remota de Windows se gestionaba a través de  llamadas remotas de procedimiento (Remote Procedure Calls), o RPCs. Estas llamadas solían  utilizar un puerto de hopping, por lo que era increíblemente difícil su gestión a través de un firewall. En contraste, con PowerShell  Remoting usted solo tiene que ocuparse de un único puerto.

Muchas organizaciones hoy en día simplemente instalan herramientas de administración en servidores y luego usan el escritorio remoto para "administrar de forma remota".En realidad es una muy mala idea, y es una de las principales razones por las que un servidor de Windows requiere tantos parches, tantos reinicios, y está expuesto a otras tantas cosas. El código necesario para soportar un GUI completo, y por lo tanto RDP, es enorme - y eso significa que los parches son inevitables. Ejecutar herramientas de administración _en el servidor_, normalmente bajo credenciales de administrador, deja abierta la puerta a un ataque.

En pocas palabras, la mayoría de las organizaciones parecen estar preocupadas por las "implicaciones" de seguridad de la conexión remota  de PowerShell. Las implicaciones son **significativas**: la comunicación remota es **mucho más segura** de lo que usted ha estado haciendo. También es más eficiente, impone menos sobrecarga en los servidores y permite que los estos funcionen con un sistema operativo más “delgado” que requiera menos parches, menos reinicios y menos Service Packs. Esos servidores también arrancarán más rápido, ejecutarán menos procesos, ejecutarán menos servicios y consumirán menos espacio de almacenamiento para el sistema operativo. También, esos servidores demandarán menos sobrecarga de memoria para el sistema operativo, lo que significa que significa que usted podrá empaquetar más de ellos en un host de virtualización. Suena horrible, ¿verdad?

## But here's the best reason
Quite simply, the main reason to enable Remoting is that _you haven't got any choice._ Microsoft has moved firmly in this direction, and enables Remoting by default on Windows Server 2012 and later. The company _disables_ Remote Desktop by default, which should tell you something. 

Further, in Nano Server, _logging onto the console isn't even an option_, whether you use Remote Desktop or not. There _is_ no local login. Remoting _is literally your only option_ for managing the server. That's going to be the case going forward.

Running a Windows environment without enabling Remoting - at least on servers - is like driving a car without wanting to depress the accelerator. It isn't much fun, and you aren't going to get very far.
