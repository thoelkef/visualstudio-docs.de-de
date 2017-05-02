---
title: "IDebugApplicationNodeEvents-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents-Schnittstelle"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents-Schnittstelle
Stellt die Ereignisschnittstelle für die `IDebugApplicationNode`\-Schnittstelle bereit.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugApplicationNodeEvents`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Behandelt das Ereignis, wenn ein untergeordneter Knoten zu einem Debuganwendungsknotenobjekt hinzugefügt wird.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Behandelt das Ereignis, wenn ein untergeordneter Knoten von einem Debuganwendungsknotenobjekt entfernt wird.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Behandelt ein Ereignis, dass das Debuganwendungsknotenobjekt von einem übergeordneten Knoten getrennt wurde.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Behandelt ein Ereignis, dass das Debuganwendungsknotenobjekt zu einem übergeordneten Knoten angefügt wurde.|  
  
## Siehe auch  
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)