---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90-enumeration"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet die gültigen Werte für Flags auf, die Ausdrucksauswertung steuern.  Diese Enumeration wird die [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration.  
  
## Syntax  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```c#  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### Parameter  
 EVAL90\_RETURNVALUE  
 Gibt an, dass der Rückgabewert falls vorhanden\) ausgewertet wird.  
  
 EVAL90\_NOSIDEEFFECTS  
 Gibt an, dass Nebeneffekte an nicht zulässig.  
  
 EVAL90\_ALLOWBPS  
 Gibt das Beenden auf Haltepunkte an.  
  
 EVAL90\_ALLOWERRORREPORT  
 Gibt die Fehlerberichterstellung für den Host zu gewährenden an.  Hauptsächlich wird für die Ausdrucksauswertung im Skript in Internet Explorer.  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 Erzwingt die als Adressen ausgewertet werden soll, Funktionen, anstatt die Funktion aufzurufen.  
  
 EVAL90\_NOFUNCEVAL  
 Verhindert Funktion ausgewertet werden.  Betrachten Sie beispielsweise das `int` Token im Ausdruck `myExpression(int) + 10`.  Diese Funktion kann als Adresse, aber nicht als Wert richtig ausgewertet werden.  
  
 EVAL90\_NOEVENTS  
 Mit Flag, dass Ereignisse, die während der Ausdrucksauswertung auftreten, Debuggen nicht auf den Manager der Sitzung \(SDM\) oder in der IDE gesendet werden sollen.  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 Aktiviert Entwurfszeitausdrucksauswertung.  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 Ermöglicht die implizite variable Build.  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 Erzwingt die Auswertung, um sofort durchgeführt wird.  Dies ist hilfreich, wenn Sie eine Anforderung, z. B. einer Benutzeranforderung instandhält.  
  
## Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)