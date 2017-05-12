---
title: "Active Script-Profilerstellung - &#220;bersicht | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Active Script-Profilerstellung"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Active Script-Profilerstellung - &#220;bersicht
[Active Script Profiler\-Schnittstelle](../winscript/reference/active-script-profiler-interfaces.md) aktivieren Profilerstellung eines Skriptmoduls zurück.  Active Script\-Profilerstellung besteht aus den folgenden Teilen:  
  
-   Sprachmodul  
  
-   Host  
  
-   Profiler  
  
## Sprachmodul  
 Das Sprachmodul führt das Skript aus.  Es stellt Methoden bereit, die die Profilerstellung des Skriptcodes aktivieren, während er ausgeführt wird.  Wenn die Profilerstellung aktiviert ist, wird das Sprachmodul den Klassenbezeichner \(CLSID\) des COM\-Objekts Profiler als Argument.  Es erstellt eine Instanz des Profilercom\-objekts und dann in den Profiler aufruft, wenn verschiedene Ereignisse auftreten.  
  
 Das Sprachmodul implementiert [IActiveScriptProfilerControl\-Schnittstelle](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Sprachenlaufzeit überprüft die JS\_PROFILER\-Umgebungsvariable auf Erstellung, ob die Profilerstellung zu bestimmen, aktiviert werden soll.  Wenn diese Variable auf den CLSID des Profilers festgelegt wird, erstellt die Sprachenlaufzeit eine Instanz des COM\-Objekts Profiler, mit dem Wert der Variablen, um zu bestimmen, die zum Erstellen der Profiler.  
  
## Host  
 Der Host stellt das Sprachmodul erstellt und enthält das Sprachmodul mit den Skripts, ausgeführt werden.  Ein Smarthost stellt auch den Dokumentenkontext, der von einem Debugger oder einen Profiler verwendet werden kann, um eine bessere Informationen bereitzustellen, wenn Sie debuggen oder ein Profil erstellen.  
  
## Profiler  
 Der Profiler empfängt die Aufrufe vom Sprachmodul, wenn verschiedene Ereignisse auftreten.  Der Profiler muss als COM\-Objekt registriert werden und muss die [IActiveScriptProfilerCallback\-Schnittstelle](../winscript/reference/iactivescriptprofilercallback-interface.md)\-Schnittstelle implementieren.  
  
## Siehe auch  
 [Active Script Profiler\-Schnittstelle](../winscript/reference/active-script-profiler-interfaces.md)