---
title: "IDebugApplicationNode::SetDocumentProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.SetDocumentProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::SetDocumentProvider"
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::SetDocumentProvider
Legt den Dokumentenanbieter für diesen Anwendungsknoten fest.  
  
## Syntax  
  
```  
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### Parameter  
 `pddp`  
 \[in\] Der Dokumentenanbieter für diesen Anwendungsknoten.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode legt den Dokumentenanbieter für diesen Anwendungsknoten fest.  
  
## Siehe auch  
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)