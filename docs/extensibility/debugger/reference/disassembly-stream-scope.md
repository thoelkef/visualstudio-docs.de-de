---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE-enumeration"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Bereich des Disassemblysdatenstroms an.  
  
## Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Mitglieder  
 DSS\_HUGE  
 Gibt an, dass der Code generiert wird, disassembliert Elementkontext Ausgabe mehr als ein Client in der Regel in einem einzelnen Aufruf abrufen kann.  
  
 DSS\_FUNCTION  
 Gibt an, dass die Funktion, die vom Code Elementkontext enthaltene disassembliert werden soll.  Gibt an, dass der Disassemblys datenstrom eine Funktion darstellt, wenn Sie die [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)\-Methode zurückgegeben werden.  
  
 DSS\_MODULE  
 Wenn Sie die `IDebugDisassemblyStream2::GetScope`\-Methode zurückgegeben werden, gibt an, dass der Disassemblys datenstrom ein Modul darstellt.  
  
 DSS\_ALL  
 Gibt die Disassembly für den gesamten Adressraum an.  
  
## Hinweise  
 Übergabe als Argument an die [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)\-Methode und die [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)\-Methode zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)