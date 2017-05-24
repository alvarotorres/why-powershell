# ¿Por qué PowerShell?

Microsoft describe PowerShell como "un shell de línea de comandos basado en tareas con un lenguaje de scripting ... construido en .NET Framework". ¿Qué es lo grandioso de PowerShell? ¿Por qué debería usarlo?

## PowerShell es un shell de línea de comandos y un lenguaje de secuencias de comandos (ambos)

“Apague incendios” rápidamente utilizando comandos existentes o personalizados de PowerShell, sin necesidad de compilar el código. Desarrolle sus soluciones desde la línea de comandos. Escriba scripts rápidamente, los usará muchas veces. Cree scripts legibles y documentados, capaces de ejecutarse en ambientes de producción. Le ayudaran a mantener sus servicios/ambientes durante años.

¿Cuál es el costo de esta inversión? Aprender PowerShell. Bastante razonable teniendo en cuenta que es probable que tenga que hacerlo independientemente de su lenguaje actual de programación, suponiendo que trabaja con el ecosistema de Microsoft.

## PowerShell can interact with a dizzying number of technologies.

The .NET Framework, the Registry, COM, WMI, ADSI. Exchange, Sharepoint, Systems Center, Hyper-V, SQL. VMware vCenter, Cisco UCS, Citrix XenApp and XenDesktop. REST APIs, XML, CSV, JSON, websites, Excel and other Office applications. C# and other languages, DLLs and other binaries, including Linux or Unix tools. A language that can work with and integrate these various technologies can be incredibly valuable.

Windows is not text based. Sooner or later you will need to do something that you can’t do with -nix tools and other text based languages. Many of the technologies that PowerShell can interact with simply do not have text based interfaces, and may not even be directly accessible from more formal languages like Perl or Python.

The moral here is that PowerShell is the best "glue" Microsoft has ever provided us for tying together disparate systems. It's better than previous Windows-based shells because it understands, and works with, the API-based nature of Windows itself, which is vastly different from what previous text-based shells did.

##PowerShell is object-based.
This gives us incredible flexibility. Filter, sort, measure, group, compare or take other actions on objects as they pass through the pipeline. Work with properties and methods rather than raw text.

If you have spent time deciphering and programmatically working with text based output, you know how frustrating it can be. What delimiter do I split on? Is there even a delimiter? What if a particular result has a blank entry for a column? Do I need to count characters in each column? Will this count vary depending on the output? With objects, this is all done for you, and makes it quite simple to tie together commands and data across various technologies.

## PowerShell isn’t going away.
Microsoft is putting its full weight behind PowerShell.

PowerShell support is a requirement in the Microsoft Common Engineering Criteria, and a Server product cannot be shipped without a PowerShell interface. That means very few Microsoft server products can't be managed by PowerShell - and the few that can't, will be able to soon.

Vendors other than Microsoft have strong support for PowerShell. This includes IBM, Cisco, Citrix, VMware, NetApp, Dell, and dozens more.

In many cases Microsoft uses PowerShell to build the GUI management consoles for its products. Some tasks can’t be performed in the GUI and can only be completed in PowerShell. This is a big deal: In an increasing number of situations, _you can't manage the product fully unless you use PowerShell._ That applies to cloud-based offerings like Azure and Office 365, too.

## Consolidate and multiply your learning

Your reward for learning PowerShell is the improved ability to control and automate the many technologies it integrates with. You can use the same set of commands to filter, export, redirect, modify, extend, and perform actions against output for all of these technologies. You can pick up  PowerShell skills and take them in any direction you need - Hyper-V, vCenter, SQL, AD, XenApp, and more.

Your reward for learning specific tools or executables such as net.exe or schtasks.exe, is the ability to work with those specific tools. With PowerShell, your learning investment blossoms into an enormous ecosystem of capability.

## In Windows, PowerShell's really the only option
VBScript is deprecated, and you're not going to see further development. VBScript was already anemic in terms of the things it could "touch," making it a poor "glue" for connecting systems and processes.

And nothing else even came close to VBScript. Python, Perl, you name it - they're great on Linux, a predominantly text-based OS, but they were nigh-useless on Windows, since they couldn't access the many and varied APIs Windows uses for management.

PowerShell consolidates all of those APIs into a single, largely-consistent interface that's focused on systems operations and administration.

