---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
Bricht einen Vorgang ab, der in einem anderen Thread ausgeführt wird.  
  
## Syntax  
  
```  
HRESULT InProgressAbort();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Vorgang kann nicht abgebrochen werden.|  
|`E_ABORT`|Der Vorgang konnte nicht abgeschlossen werden.|  
  
## Hinweise  
 Der Prozessdebug\-Manager ruft diese Methode aus dem Debuggerthread an, um einen Vorgang abbrechen, der in einem anderen Thread ausgeführt wird.  
  
 Wenn die `InProgressAbort`\-Methode den Vorgang nicht abschließen kann, gibt sie `E_ABORT` so schnell wie möglich zurück.  Diese Methode kann `E_NOTIMPL` zurückgeben, wenn der Vorgang nicht abgebrochen werden kann.  
  
## Siehe auch  
 [IDebugSyncOperation\-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)