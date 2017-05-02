---
title: "IMachineDebugManagerCookie-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie-Schnittstelle"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie-Schnittstelle
Wie die `IMachineDebugManager`\-Schnittstelle, Debuggen die `IMachineDebugManagerCookie`\-Schnittstellenunterstützung Cookies.  
  
 Diese Schnittstelle \(zusammen mit der `IDebugCookie`\-Schnittstelle\) können Skripts in einem Skriptdebuggerprozess, ohne zu erfordern, dass der Debugger diese Skripts verfolgen.  
  
 Ein `IDebugCookie::SetDebugCookie` Skriptdebugger ruft die Methode auf dem Prozessdebug\-Manager an \(PDM\).  Anschließend sendet das PDM das Cookie zusammen mit jeder Anforderung, eine Skript\-Anwendung in oder aus dem Debuggen Machine Manager \(MDM\), mithilfe der Methoden der Schnittstelle `IMachineDebugManagerCookie` hinzuzufügen oder zu entfernen.  Das MDM benachrichtigt dann jeden Debugger über der Änderung, mit Ausnahme der, die das Cookie verfügt.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IMachineDebugManagerCookie`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Fügt eine Anwendung der Liste der laufenden Anwendung hinzu.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Gibt einen Enumerator der aktuellen Liste der ausgeführten Anwendungen zurück.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Entfernt eine Anwendung aus der Liste der laufenden Anwendung.|  
  
## Siehe auch  
 [IMachineDebugManager\-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie\-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)