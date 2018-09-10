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
ms.openlocfilehash: 97d39a171d812915a1cf3c1c6450c73098067949
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284197"
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
 [crt_dbg2-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
