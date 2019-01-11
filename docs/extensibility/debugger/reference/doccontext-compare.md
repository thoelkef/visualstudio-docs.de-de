---
title: DOCCONTEXT_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0fd536404778b5f61e859da28d9e4fec1df32d3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851059"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Gibt die Kriterien zum Vergleichen von zwei dokumentenkontexte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Member  
 DOCCONTEXT_EQUAL  
 Finden Sie in der Liste, die den Zielkontext-Dokument entspricht der ersten Dokumentkontext.  
  
 DOCCONTEXT_LESS_THAN  
 Finden Sie in der Liste, die kleiner ist als den Zielkontext für das Dokument den ersten Dokumentenkontext.  
  
 DOCCONTEXT_GREATER_THAN  
 Finden Sie in der Liste, die über den Dokument-Zielkontext liegt der ersten Dokumentkontext.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Finden Sie in der Liste, die in demselben Dokument wie den Zielkontext für das Dokument ist der ersten Dokumentkontext.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) Methode.  
  
 Diese Werte werden verwendet, eine Vergleichskriterien für die Suche nach den ersten Dokumentenkontext in einer Liste an. Ein Dokumentenkontext erhält eine Liste der dokumentenkontexte selbst gegen durch Vergleichen der `IDebugDocumentContext2::Compare` Methode. Das erste Dokumentenkontext, in der Liste, die für die der Vergleichsoperator ist `true` wird zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)