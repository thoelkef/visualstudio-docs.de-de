---
title: "IDebugApplication::AddStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::AddStackFrameSniffer"
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::AddStackFrameSniffer
Fügt einen Stapelrahmenenumeratoranbieter dieser Anwendung hinzu.  
  
## Syntax  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### Parameter  
 `pdsfs`  
 \[in\] Der dieser Anwendung hinzuzufügen, Stapelrahmenenumeratoranbieter.  
  
 `pdwCookie`  
 \[out\] Ein Cookie, das verwendet wird, um diesen Stapelrahmenenumeratoranbieter von der Anwendung zu entfernen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Obwohl Sprachmodule normalerweise diese Methode aufrufen, um ihre Stapelrahmen dem Debugger verfügbar zu machen, können von anderen Entitäten, Stapelrahmen verfügbar zu machen.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer\-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)