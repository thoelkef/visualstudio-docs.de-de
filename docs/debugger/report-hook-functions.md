---
title: Hookfunktionen für Berichte | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0bb14b47fb17c4d59089aafa123115b85ab9342
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729868"
---
# <a name="report-hook-functions"></a>Hookfunktionen für Berichte
Eine mithilfe von [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook) installierte Hookfunktion für Berichte wird jedes Mal aufgerufen, wenn durch [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ein Debugbericht generiert wird. Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen. Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 Der Zeiger, den Sie an **_CrtSetReportHook** übergeben, ist vom Typ **_CRT_REPORT_HOOK**, wie in CRTDBG definiert. Micha

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Wenn die Hookfunktion von der Laufzeitbibliothek aufgerufen wird, enthält das *nRptType*-Argument die Berichtskategorie ( **_CRT_WARN**, **_CRT_ERROR** oder **_CRT_ASSERT**); *szMsg* enthält einen Zeiger auf eine vollständig assemblierte Berichtsmeldungszeichenfolge, und *retVal* gibt an, ob `_CrtDbgReport` nach der Berichtgenerierung die normale Ausführung fortsetzen oder den Debugger starten soll. (Bei einem *retVal*-Wert von 0 (null) wird die Ausführung fortgesetzt, und bei einem Wert von 1 wird der Debugger gestartet.)

 Wenn die betreffende Meldung vollständig vom Hook behandelt wird, sodass kein weiterer Bericht erforderlich ist, muss er **TRUE** zurückgeben. Wenn **FALSE** zurückgegeben wird, gibt `_CrtDbgReport` die Meldung wie üblich aus.

## <a name="see-also"></a>Siehe auch
- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)
- [crt_dbg2, Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
