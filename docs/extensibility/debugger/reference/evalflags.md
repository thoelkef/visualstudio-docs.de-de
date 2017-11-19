---
title: EVALFLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVALFLAGS
helpviewer_keywords: EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45bef946605818f11d0199600849fd49b5463ab8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="evalflags"></a>EVALFLAGS
Gibt Flags an, die Auswertung von Ausdrücken zu steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EVALFLAGS {  
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
public enum enum_EVALFLAGS {  
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
 Gibt an, dass Nebeneffekte nicht zulässig.  
  
 EVAL_ALLOWBPS  
 Gibt den Beenden an Haltepunkten an.  
  
 EVAL_ALLOWERRORREPORT  
 Gibt an, Fehlerberichte an den Host zugelassen werden. In erster Linie verwendet für die Auswertung von Ausdrücken im Skript in Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Erzwingt, dass Funktionen, die als Adressen, statt den Funktionsaufruf ausgewertet werden.  
  
 EVAL_NOFUNCEVAL  
 Verhindern Sie, dass Funktion ausgewertet wird. Betrachten Sie beispielsweise die `int` token im Ausdruck `myExpression(int) + 10`. Diese Funktion kann als eine Adresse, jedoch nicht als Wert richtig ausgewertet werden.  
  
 EVAL_NOEVENTS  
 Kennzeichen Sie, um anzugeben, dass Ereignisse während der Auswertung von Ausdrücken nicht zu der Sitzung Debug-Manager (SDM) oder der IDE gesendet werden sollen.  
  
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