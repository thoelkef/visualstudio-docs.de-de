---
title: STEPKIND | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c11bae91dfac04dd71932aeef949bae5c15de17e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920338"
---
# <a name="stepkind"></a>STEPKIND
Gibt den Schritt für die schrittweise Ausführung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Member  
 STEP_INTO  
 Eine Funktion in Einzelschritten.  
  
 SCHRITTWEITE  
 Schritte für eine Funktion.  
  
 STEP_OUT  
 Die Schritte aus einer Funktion.  
  
 STEP_BACKWARDS  
 Schritte nach hinten an eine Funktion.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)