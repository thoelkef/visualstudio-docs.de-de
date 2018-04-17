---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b238012a844016324bbdee4df3cc167051815f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Gibt die Bedingung, die die Anzahl der Breakpoint-Übergabe, die bewirkt, den Haltepunkt dass ausgelöst zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 BP_PASSCOUNT_NONE  
 Gibt keine Haltepunkt Pass Count-Stil.  
  
 BP_PASSCOUNT_EQUAL  
 Legt den Haltepunkt Pass Anzahl Stil gleich. Der Haltepunkt ausgelöst wird, wenn die Anzahl der Häufigkeit, mit die der Breakpoint erreicht wird die Anzahl der Durchläufe entspricht.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Legt den Haltepunkt Pass Count-Stil auf gleich oder größer fest. Der Haltepunkt ausgelöst wird, wenn die Anzahl der Häufigkeit, mit die der Breakpoint erreicht wird, gleich oder größer als die Anzahl der erfolgreich ist.  
  
 BP_PASSCOUNT_MOD  
 Gibt an, ein modulo Durchläufe. Beispielsweise ist die Anzahl der Durchläufe des Typs `BP_PASSCOUNT_MOD` und der Wert für die Übergabe ist 4, der Haltepunkt ausgelöst, die jedes Mal, wenn die Trefferanzahl ein Vielfaches von 4 ist.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `stylePassCount` Mitglied der [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die wiederum Mitglied ist die [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)