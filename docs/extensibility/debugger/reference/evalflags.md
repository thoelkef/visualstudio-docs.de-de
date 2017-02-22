---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "EVALFLAGS-enumeration"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt Flags an, die Ausdrucksauswertung steuern.  
  
## Syntax  
  
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
  
```c#  
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
  
## Mitglieder  
 EVAL\_RETURNVALUE  
 Gibt an, dass der Rückgabewert falls vorhanden\) ausgewertet wird.  
  
 EVAL\_NOSIDEEFFECTS  
 Gibt an, dass Nebeneffekte an nicht zulässig.  
  
 EVAL\_ALLOWBPS  
 Gibt das Beenden auf Haltepunkte an.  
  
 EVAL\_ALLOWERRORREPORT  
 Gibt Problemberichte zu gewährenden an den Host an.  Hauptsächlich wird für die Ausdrucksauswertung im Skript in Internet Explorer.  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 Erzwingt die als Adressen ausgewertet werden soll, Funktionen, anstatt die Funktion aufzurufen.  
  
 EVAL\_NOFUNCEVAL  
 Verhindert Funktion ausgewertet werden.  Betrachten Sie beispielsweise das `int` Token im Ausdruck `myExpression(int) + 10`.  Diese Funktion kann als Adresse, aber nicht als Wert richtig ausgewertet werden.  
  
 EVAL\_NOEVENTS  
 Mit Flag, dass Ereignisse, die während der Ausdrucksauswertung auftreten, Debuggen nicht auf den Manager der Sitzung \(SDM\) oder in der IDE gesendet werden sollen.  
  
## Hinweise  
 Diese Flags werden als Argument an den [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) und [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)\-Methode übergeben.  
  
 Diese Flags werden mit einem bitweisen OR\-Operation kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)