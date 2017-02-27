---
title: "CANSTOP_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CANSTOP_REASON"
helpviewer_keywords: 
  - "CANSTOP_REASON-enumeration"
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird verwendet, um zu bestimmen, ob ein Programm Ausführung beenden kann, nachdem es einen bestimmten Punkt in der Ausführung erreicht hat.  
  
## Syntax  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## Mitglieder  
 CANSTOP\_ENTRYPOINT  
 Gibt den Einstiegspunkt des angegebenen Programms an.  
  
 CANSTOP\_STEPIN  
 Gibt schrittweise in eine benutzerdefinierte Funktion.  
  
## Hinweise  
 Werden z. B. ein Argument an die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)\-Methode, um dem Sitzungs\-Debugen Manager \(SDM\) zu bestätigen, wenn geeignet ist, beenden, nachdem es den Einstiegspunkt des Programms erreicht wurde oder nachdem es in eine Funktion oder Methode aufgetreten ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)