---
title: CONTEXT_COMPARE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 869cc102f3c78c6ad074648d9715af124cf964e9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284764"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Kriterien zum Vergleichen von zwei Speicher Kontexten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Member  
 CONTEXT_EQUAL  
 Finden Sie den Speicherkontext für ersten, in der Liste, die den Arbeitsspeicher Zielkontext entspricht.  
  
 CONTEXT_LESS_THAN  
 Finden Sie den Speicherkontext für ersten, in der Liste, die kleiner als den Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_GREATER_THAN  
 Finden Sie die ersten Arbeitsspeicher-Kontext, in der Liste aus, die den Zielkontext der Arbeitsspeicher größer ist.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Finden Sie den ersten Arbeitsspeicher-Kontext, in der Liste, die kleiner als oder gleich den Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Finden Sie den Speicherkontext für ersten, in der Liste, die größer als oder gleich den Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_SAME_SCOPE  
 Finden Sie den Speicherkontext für ersten, in der Liste, die im gleichen Bereich wie den Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_SAME_FUNCTION  
 Finden Sie den Speicherkontext für ersten, in der Liste, die in die gleiche Funktion wie der Zielbereich für den Arbeitsspeicher ist.  
  
 CONTEXT_SAME_MODULE  
 Finden Sie den Speicherkontext für ersten, in der Liste, die im selben Modul wie den Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_SAME_PROCESS  
 Finden Sie den Speicherkontext für ersten, in der Liste, die in demselben Prozess wie den Zielkontext der Arbeitsspeicher ist.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) Methode.  
  
 Diese Werte werden zum ersten Arbeitsspeicher Kontext in einer Liste zu suchen, die die angegebenen Vergleichskriterien entspricht. Ein Kontext an Arbeitsspeicher erhält eine Liste von Kontexten, Speicher selbst vor über vergleichen die `IDebugMemoryContext2::Compare` Methode. Die erste Arbeitsspeicher-Kontext, in der Liste, die für die der Vergleichsoperator ist `true` wird zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

