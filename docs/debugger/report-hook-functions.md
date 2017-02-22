---
title: "Hookfunktionen f&#252;r Berichte | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport-Funktion"
  - "_CrtSetReportHook-Funktion"
  - "Debugger, Berichtshookfunktionen"
  - "Debuggen [C++], Hookfunktionen"
  - "Hooks, Bericht"
  - "Speicherreservierung, Debugheap"
  - "Berichtshookfunktionen"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Hookfunktionen f&#252;r Berichte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine mithilfe von [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook) installierte Hookfunktion für Berichte wird jedes Mal aufgerufen, wenn durch [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ein Debugbericht generiert wird.  Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen.  Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Der an **\_CrtSetReportHook** übergebene Zeiger ist vom Typ **\_CRT\_REPORT\_HOOK**, wie in CRTDBG.H definiert:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Wenn die Hookfunktion von der Laufzeitbibliothek aufgerufen wird, enthält das *nRptType\-*Argument die Berichtskategorie \(**\_CRT\_WARN**, **\_CRT\_ERROR** oder **\_CRT\_ASSERT**\); *szMsg* enthält einen Zeiger auf eine vollständig assemblierte Berichtsmeldungszeichenfolge, und *retVal* gibt an, ob `_CrtDbgReport` nach der Berichtgenerierung die normale Ausführung fortsetzen oder den Debugger starten soll. \(Bei einem *retVal*\-Wert von 0 \(null\) wird die Ausführung fortgesetzt und bei einem Wert von 1 wird der Debugger gestartet.\)  
  
 Wenn die betreffende Meldung vollständig vom Hook behandelt wird, sodass kein weiterer Bericht erforderlich ist, muss er **TRUE** zurückgeben.  Wenn **FALSE** zurückgegeben wird, gibt `_CrtDbgReport` die Meldung wie üblich aus.  
  
## Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/de-de/21e1346a-6a17-4f57-b275-c76813089167)