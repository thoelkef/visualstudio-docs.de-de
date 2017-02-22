---
title: "CONNECTION_PROTOCOL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONNECTION_PROTOCOL"
helpviewer_keywords: 
  - "CONNECTION_PROTOCOL-enumeration"
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt das Protokoll an, das verwendet wird, um zwischen einem Server und dem Debuggen die Option Debuggen Paket \(DE\) zu kommunizieren.  
  
## Syntax  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```c#  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### Parameter  
 CONNECTION\_NONE  
 Keine Beziehung entspricht einem Server hergestellt wurde.  
  
 CONNECTION\_UNKNOWN  
 Eine Verbindung wird hergestellt, doch sie wird von einem unbekannten Typ.  
  
 CONNECTION\_LOCAL  
 Verbindung mit einem lokalen Server.  
  
 CONNECTION\_PIPE  
 Verbindung wurde durch eine benannte Pipe.  
  
 CONNECTION\_TCPIP  
 Anschlussnutzungen TCP\/IP.  
  
 CONNECTION\_HTTP  
 Anschlussnutzungen \(HTTP über einen Webserver\).  
  
 CONNECTION\_OTHER  
 Ein anderer Typ Verbindung hergestellt ist \(Dieser Wert wird derzeit nicht verwendet\).  
  
## Hinweise  
 Diese Werte werden von der [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)