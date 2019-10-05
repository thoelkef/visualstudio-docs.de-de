---
title: EVALFLAGS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6ee00402c13b2a79e4e6757a127211eda9c3c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149383"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt Flags an, die Auswertung des Ausdrucks steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Member  
 EVAL_RETURNVALUE  
 Gibt an, dass der Rückgabewert, sofern vorhanden, ausgewertet werden.  
  
 EVAL_NOSIDEEFFECTS  
 Gibt an, dass Nebenwirkungen nicht zugelassen werden.  
  
 EVAL_ALLOWBPS  
 Gibt die für Haltepunkte wird beendet.  
  
 EVAL_ALLOWERRORREPORT  
 Gibt die Windows-Fehlerberichterstattung mit dem Host zulässig sein soll. In erster Linie verwendet für die Auswertung des Ausdrucks im Skript in Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Erzwingt, dass Funktionen wie Adressen, anstelle von Aufrufen der Funktion ausgewertet werden soll.  
  
 EVAL_NOFUNCEVAL  
 Verhindert, dass Funktion ausgewertet wird. Betrachten Sie beispielsweise die `int` token im Ausdruck `myExpression(int) + 10`. Diese Funktion kann als eine Adresse, aber nicht als Wert ordnungsgemäß ausgewertet werden.  
  
 EVAL_NOEVENTS  
 Flag, um anzugeben, dass Ereignisse während der Auswertung des Ausdrucks nicht sitzungsbasierter Debug-Manager (SDM) oder die IDE gesendet werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden übergeben, als Argument an die [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) und [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) Methoden.  
  
 Diese Flags können mit einem bitweisen OR kombiniert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
