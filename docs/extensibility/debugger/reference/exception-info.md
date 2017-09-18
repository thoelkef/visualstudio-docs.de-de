---
title: "EXCEPTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "EXCEPTION_INFO-Struktur"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgelöst, die vom Programm, das gedebuggt wird.  
  
## Syntax  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## Mitglieder  
 pProgram  
 Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm darstellt, in der die Ausnahme aufgetreten ist.  
  
 bstrProgramName  
 Der Name des Programms, in der die Ausnahme aufgetreten ist.  
  
 bstrExceptionName  
 Der Name der Ausnahme.  
  
 dwCode  
 Der Identifikation von Code für die Ausnahme oder Laufzeitfehler.  
  
 dwState  
 Ein Wert aus der [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)\-Enumeration, die den Zustand der Ausnahme definiert.  
  
 guidType  
 Die GUID\-Sprachen\-ID, entweder `guidLang` oder `guidEng`.  
  
## Hinweise  
 Diese Struktur wird als Parameter an [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) und [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)\-Methode übergeben.  Diese Struktur wird auch der Methode übergeben [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) ausgefüllt werden soll.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)