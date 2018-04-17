---
title: Hook Berichtsfunktionen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7de5ae8611a3577902d5a6a893d7971ac40cc88b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="report-hook-functions"></a>Hookfunktionen für Berichte
Einer Hookfunktion mithilfe von installiert [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), wird jedes Mal aufgerufen [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ein Debugbericht generiert. Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen. Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Der Zeiger, die Sie zum übergeben **_CrtSetReportHook** ist vom Typ **_CRT_REPORT_HOOK**, wie in CRTDBG.H definiert. H  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Wenn die Laufzeitbibliothek, die Hookfunktion aufruft die *nRptType* Argument enthält die Kategorie des Berichts (**_CRT_WARN**, **_CRT_ERROR**, oder **_CRT _ASSERT**), *wird* enthält einen Zeiger auf eine Meldungszeichenfolge Berichtskategorie und *RetVal* gibt an, ob `_CrtDbgReport` die normale Ausführung fortsetzen soll nach der Generierung der Bericht "oder" Starten des Debuggers. (Ein *RetVal* Wert von 0 (null) setzt die Ausführung, der Wert 1 wird der Debugger gestartet.)  
  
 Wenn die Hookfunktion betreffende Meldung vollständig behandelt, sodass kein weiterer Bericht erforderlich ist, sollte er zurück **"true"**. Wenn zurückgegeben **"false"**, `_CrtDbgReport` meldet die Nachricht normalerweise.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)