---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2be5678704e9a5899c4ce7f5caba8cec1d8a21e6
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# CONNECTION_PROTOCOL
Gibt an, das Protokoll für die Kommunikation zwischen einem Debug-Server und das debugpaket (DE) verwendet wird.  
  
## Syntax  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### Parameter  
 CONNECTION_NONE  
 Mit einem Server hat keine Verbindung hergestellt wurde.  
  
 CONNECTION_UNKNOWN  
 Eine Verbindung hergestellt wurde, jedoch einen unbekannten Typ ist.  
  
 CONNECTION_LOCAL  
 Verbindung ist mit einem lokalen Server.  
  
 CONNECTION_PIPE  
 Verbindung wird über eine named Pipe.  
  
 CONNECTION_TCPIP  
 Verbindung wird die TCP/IP verwendet.  
  
 CONNECTION_HTTP  
 Verbindung wird HTTP (über einen Webserver) verwendet.  
  
 CONNECTION_OTHER  
 Eine andere Art von Verbindung hergestellt wurde (dieser Wert wird derzeit nicht verwendet).  
  
## Hinweise  
 Diese Werte werden zurückgegeben, aus der [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
