---
title: "IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsCurrentThread"
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsCurrentThread
Bestimmt, ob dieser Thread der momentan ausgeführten Thread ist.  
  
## Syntax  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode erfolgreich war und dies ist der momentan ausgeführten Thread.|  
|`S_FALSE`|Dies ist nicht der momentan ausgeführten Thread.|  
  
## Hinweise  
 Diese Methode bestimmt, wenn dieser Thread der momentan ausgeführten Thread ist.  
  
## Siehe auch  
 [IDebugApplicationThread\-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)