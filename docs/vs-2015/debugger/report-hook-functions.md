---
title: Melden Sie Hook-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557790edc774bab9db43830a4f5fc3e21cfc9758
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279447"
---
# <a name="report-hook-functions"></a>Hookfunktionen für Berichte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Hookfunktion mithilfe von installiert [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), wird immer dann aufgerufen [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) ein Debugbericht generiert. Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen. Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Der Zeiger, der Sie übergeben **_CrtSetReportHook** ist vom Typ **_CRT_REPORT_HOOK**, wie in CRTDBG.H definiert. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, die *nRptType* Argument enthält die Kategorie des Berichts (**_CRT_WARN**, **_CRT_ERROR**, oder **_CRT _ASSERT**), *wird* enthält einen Zeiger auf eine Berichtskategorie-Meldungszeichenfolge und *RetVal* gibt an, ob `_CrtDbgReport` die normale Ausführung fortsetzen soll nach dem Generieren des Berichts oder den Start des Debuggers. (Ein *RetVal* Wert 0 (null) wird die Ausführung fortgesetzt, die der Wert 1 wird der Debugger gestartet.)  
  
 Wenn der Hook betreffende Meldung vollständig behandelt wird, sodass kein weiterer Bericht erforderlich ist, sollte es zurückgeben **"true"**. Wenn sie zurückgibt **"false"**, `_CrtDbgReport` wird die Nachricht normalerweise.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



