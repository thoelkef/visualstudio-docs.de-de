---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DOCCONTEXT_COMPARE
helpviewer_keywords: DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d2882ebf3a1b21a4921f863496a42ac50ac1b2fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Gibt die Kriterien zum Vergleichen von zwei Dokument Kontexten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Member  
 DOCCONTEXT_EQUAL  
 Finden Sie den ersten Dokumentenkontext, in der Liste, die das Dokument Zielkontext gleich ist.  
  
 DOCCONTEXT_LESS_THAN  
 Finden Sie den ersten Dokumentenkontext, in der Liste, die kleiner als der Zielkontext Dokument ist.  
  
 DOCCONTEXT_GREATER_THAN  
 Finden Sie den ersten Dokumentenkontext, in der Liste, die größer als die Zielkontext Dokument ist.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Finden Sie den ersten Dokumentenkontext, in der Liste, die im selben Dokument wie das Dokument Zielkontext ist.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) Methode.  
  
 Diese Werte werden verwendet, eine Vergleichskriterien für die Suche nach den ersten Dokumentenkontext in einer Liste angeben. Ein Dokumentenkontext empfängt eine Liste von Kontexten Dokument selbst gegen durch Vergleichen der `IDebugDocumentContext2::Compare` Methode. Die ersten Dokumentenkontext in der Liste aus, für die der Vergleichsoperator ist `true` wird zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)