---
title: CONTEXT_COMPARE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beba9f612024a63f8f302411982442df19e0bbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Gibt die Kriterien zum Vergleichen von zwei Speicher Kontexten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die den Zielkontext Arbeitsspeicher entspricht.  
  
 CONTEXT_LESS_THAN  
 Finden Sie den ersten Arbeitsspeicher-Kontext, in der Liste, die kleiner als der Arbeitsspeicher Zielkontext ist.  
  
 CONTEXT_GREATER_THAN  
 Finden Sie den ersten Arbeitsspeicher-Kontext, in der Liste, die größer als der Arbeitsspeicher Zielkontext ist.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die kleiner als oder gleich der Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die größer als oder gleich der Zielkontext der Arbeitsspeicher ist.  
  
 CONTEXT_SAME_SCOPE  
 Finden Sie den ersten Arbeitsspeicher-Kontext, in der Liste, die im selben Bereich wie der Arbeitsspeicher Zielkontext ist.  
  
 CONTEXT_SAME_FUNCTION  
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die in die gleiche Funktion wie der Zielbereich Arbeitsspeicher ist.  
  
 CONTEXT_SAME_MODULE  
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die im selben Modul wie der Arbeitsspeicher Zielkontext ist.  
  
 CONTEXT_SAME_PROCESS  
 Finden Sie den ersten Kontext für den Arbeitsspeicher, in der Liste, die in demselben Prozess wie der Arbeitsspeicher Zielkontext ist.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) Methode.  
  
 Diese Werte werden verwendet, um den ersten Speicherkontext in einer Liste zu suchen, die den angegebenen Vergleichskriterien erfüllt. Ein Speicherkontext empfängt eine Liste von Arbeitsspeicher Kontexten selbst gegen durch Vergleichen der `IDebugMemoryContext2::Compare` Methode. Die erste Arbeitsspeicher-Kontext, in der Liste aus, für die der Vergleichsoperator ist `true` wird zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)