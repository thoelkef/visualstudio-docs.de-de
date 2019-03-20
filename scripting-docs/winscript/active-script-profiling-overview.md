---
title: Active Script-Profilerstellung – Übersicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d03ab4df7a41fe6513a18446d26e33e9856d1183
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149613"
---
# <a name="active-script-profiling-overview"></a>Active Script-Profilerstellung - Übersicht
Die [Active Script Profiler-Schnittstelle](../winscript/reference/active-script-profiler-interfaces.md) erlaubt die Profilerstellung einer Skript-Engine. Die Active Script-Profilerstellung umfasst folgende Teile:  
  
-   Sprach-Engine  
  
-   Host  
  
-   Profiler  
  
## <a name="language-engine"></a>Sprach-Engine  
 Die Sprach-Engine führt das Skript aus. Es bietet Methoden, die die Profilerstellung des Skriptcodes aktiviert, wenn dieser ausgeführt wird. Wenn die Profilerstellung aktiviert ist, nimmt die Sprach-Engine die Klassen-ID (CLSID) des COM-Profilerobjekts als Argument. Es erstellt eine Instanz des COM-Profilerstellungsobjekts und führt einen Aufruf im Profiler auf, wenn unterschiedliche Ereignisse auftreten.  
  
 Die Sprach-Engine implementiert die [IActiveScriptProfilerControl-Schnittstelle](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Die [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Language Runtime überprüft die Umgebungsvariable JS_PROFILER bei der Erstellung, um zu bestimmen, ob die Profilerstellung aktiviert werden soll. Wenn diese Variable auf die CLSID des Profilers festgelegt ist, erstellt die Language Runtime eine Instanz des COM-Profilerobjekts unter Verwendung des Werts der Variable, um festzustellen, welcher Profiler erstellt werden soll.  
  
## <a name="host"></a>Host  
 Der Host erstellt die Sprach-Engine und stellt sie mit Skripts bereit, die ausgeführt werden sollen. Ein Smarthost stellt ebenso den Dokumentkontext bereit, der von einem Debugger oder Profiler verwendet werden kann, damit bessere Informationen beim Debuggen oder bei der Profilerstellung bereitgestellt werden können.  
  
## <a name="profiler"></a>Profiler  
 Wenn verschiedene Ereignisse eintreten, erhält der Profiler die Aufrufe der Sprach-Engine. Der Profiler muss als COM-Objekt registriert sein und die [IActiveScriptProfilerCallback-Schnittstelle](../winscript/reference/iactivescriptprofilercallback-interface.md) implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../winscript/reference/active-script-profiler-interfaces.md)