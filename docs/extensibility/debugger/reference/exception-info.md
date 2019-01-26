---
title: EXCEPTION_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e255695cd461f5c272bc65f695d8935ab892d034
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960242"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgegeben, die von der zu debuggende Programm wird ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Member  
 pProgram  
 Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in dem die Ausnahme aufgetreten ist.  
  
 bstrProgramName  
 Der Name des Programms in der die Ausnahme aufgetreten ist.  
  
 bstrExceptionName  
 Der Name der Ausnahme.  
  
 dwCode  
 Die ID-Code für die Ausnahme oder ein Laufzeit-Fehler.  
  
 dwState  
 Ein Wert aus der [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Enumeration, die den Zustand der Ausnahme definiert.  
  
 guidType  
 Die GUID für die Sprache, entweder `guidLang` oder `guidEng`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird als Parameter an übergeben die [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) und [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Methoden. Diese Struktur wird ebenfalls übergeben, um die [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) Methode gefüllt werden soll.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)