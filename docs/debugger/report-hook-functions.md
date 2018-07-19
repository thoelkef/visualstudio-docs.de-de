---
title: Melden Sie Hook-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 093b7732f78f7257a2e58812ca2697496d65682f
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056481"
---
# <a name="report-hook-functions"></a>Hookfunktionen für Berichte
Eine Hookfunktion mithilfe von installiert [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), wird immer dann aufgerufen [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ein Debugbericht generiert. Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen. Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Der Zeiger, der Sie übergeben **_CrtSetReportHook** ist vom Typ **_CRT_REPORT_HOOK**, wie in CRTDBG.H definiert. H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, die *nRptType* Argument enthält die Kategorie des Berichts (**_CRT_WARN**, **_CRT_ERROR**, oder **_CRT _ASSERT**), *wird* enthält einen Zeiger auf eine Berichtskategorie-Meldungszeichenfolge und *RetVal* gibt an, ob `_CrtDbgReport` die normale Ausführung fortsetzen soll nach dem Generieren des Berichts oder den Start des Debuggers. (Ein *RetVal* Wert 0 (null) wird die Ausführung fortgesetzt, die der Wert 1 wird der Debugger gestartet.)  
  
 Wenn der Hook betreffende Meldung vollständig behandelt wird, sodass kein weiterer Bericht erforderlich ist, sollte es zurückgeben **"true"**. Wenn sie zurückgibt **"false"**, `_CrtDbgReport` wird die Nachricht normalerweise.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)
