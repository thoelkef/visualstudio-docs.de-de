---
title: "IMachineDebugManagerEvents-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerEvents-Schnittstelle"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents-Schnittstelle
Signaländerungen in der Liste der laufenden Anwendung, die von ausgeführt wird, bearbeiten Debug\- Manager Computer.  Diese Schnittstelle kann vom Debugger IDE verwendet werden, um eine dynamische Liste von Anwendungen anzuzeigen.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IMachineDebugManagerEvents`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Behandelt das Ereignis, wenn eine Anwendung zur Liste der laufenden Anwendung hinzugefügt wird.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Behandelt das Ereignis, wenn eine Anwendung von der Liste der laufenden Anwendung entfernt wird.|