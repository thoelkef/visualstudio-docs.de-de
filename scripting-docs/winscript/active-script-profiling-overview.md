---
title: "Active Script-Profilerstellung – Übersicht | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiling-overview"></a>Active Script-Profilerstellung - Übersicht
Die [Active Script Profiler-Schnittstelle](../winscript/reference/active-script-profiler-interfaces.md) erlaubt die Profilerstellung eines Skriptmoduls. Die Active Script-Profilerstellung umfasst folgende Teile:  
  
-   Sprachmodul  
  
-   Host  
  
-   Profiler  
  
## <a name="language-engine"></a>Sprachmodul  
 Das Sprachmodul führt das Skript aus. Es bietet Methoden, die die Profilerstellung des Skriptcodes aktiviert, wenn dieser ausgeführt wird. Wenn die Profilerstellung aktiviert ist, nimmt das Sprachmodul die Klassen-ID (CLSID) des COM-Profilerobjekts als Argument. Es erstellt eine Instanz des COM-Profilerstellungsobjekts und führt einen Aufruf im Profiler auf, wenn unterschiedliche Ereignisse auftreten.  
  
 Das Sprachmodul implementiert die [IActiveScriptProfilerControl-Schnittstelle](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Language Runtime überprüft die Umgebungsvariable JS_PROFILER bei der Erstellung, um zu bestimmen, ob die Profilerstellung aktiviert werden soll. Wenn diese Variable auf die CLSID des Profilers festgelegt ist, erstellt die Language Runtime eine Instanz des COM-Profilerobjekts unter Verwendung des Werts der Variable, um festzustellen, welcher Profiler erstellt werden soll.  
  
## <a name="host"></a>Host  
 Der Host erstellt das Sprachmodul und stellt es mit Skripts bereit, die ausgeführt werden sollen. Ein Smarthost stellt ebenso den Dokumentkontext bereit, der von einem Debugger oder Profiler verwendet werden kann, damit bessere Informationen beim Debuggen oder bei der Profilerstellung bereitgestellt werden können.  
  
## <a name="profiler"></a>Profiler  
 Wenn verschiedene Ereignisse eintreten, erhält der Profiler die Aufrufe des Sprachmoduls. Der Profiler muss als COM-Objekt registriert sein und die [IActiveScriptProfilerCallback-Schnittstelle](../winscript/reference/iactivescriptprofilercallback-interface.md) implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../winscript/reference/active-script-profiler-interfaces.md)