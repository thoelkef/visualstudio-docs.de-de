---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
Kraftausführung, um der Vervollständigung so fortzusetzen, wie möglich an den angegebenen Codekontext, im Kontext des angegebenen Frames.  
  
## Syntax  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### Parameter  
 `pStackFrame`  
 \[in\] Das Stapelrahmenobjekt.  Dieses Argument kann NULL sein, das den aktuellen Stapelrahmen bedeutet sollte verwendet werden.  
  
 `pCodeContext`  
 \[in\] Der Codekontext.  Dieses Argument kann NULL sein, das den aktuellen Codekontext bedeutet sollte verwendet werden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erzwingt Ausführung, um Abschluss so fortzusetzen, wie möglich an den Codekontext, der von `pCodeContext`, im Kontext der Rahmen angegeben wird, die von `pStackFrame` angegeben werden.  Jeder dieser Argumente ist möglicherweise `NULL` und stellt den aktuellen Frame oder den Kontext dar.  
  
## Siehe auch  
 [IRemoteDebugApplicationThread\-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)