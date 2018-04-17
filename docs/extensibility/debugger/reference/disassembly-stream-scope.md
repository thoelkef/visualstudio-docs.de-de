---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0c72d0f14da9840c0a77d5ae88cb0acb5b54cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Gibt den Bereich des Datenstroms Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 DSS_HUGE  
 Gibt an, dass die Disassemblierung der Codekontext Ausgabewerte erzeugt würde mehr als ein Client in der Regel in einem einzigen Aufruf abrufen möchten.  
  
 DSS_FUNCTION  
 Gibt an, dass die Funktion enthaltenen Codekontext disassembliert werden sollte. Gibt an, dass die Disassembly-Datenstrom eine Funktion darstellt, wenn vom der [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) Methode.  
  
 DSS_MODULE  
 Nach der Rückgabe durch die `IDebugDisassemblyStream2::GetScope` -Methode, gibt an, dass die Disassembly Stream ein Moduls darstellt.  
  
 DSS_ALL  
 Gibt die Disassembly für im gesamten Adressraum.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) Methode und zurückgegeben, indem die [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) Methode.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)