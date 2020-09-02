---
title: Hookfunktionen für Berichte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687512"
---
# <a name="report-hook-functions"></a>Hookfunktionen für Berichte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine mithilfe von [_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509) installierte Hookfunktion für Berichte wird jedes Mal aufgerufen, wenn durch [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) ein Debugbericht generiert wird. Sie können mit dieser Funktion u. a. Berichte filtern, um bestimmte Reservierungstypen herauszustellen. Der Prototyp einer Hookfunktion für Berichte sollte etwa wie folgt aussehen:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Der an **_CrtSetReportHook** übergebene Zeiger ist vom Typ **_CRT_REPORT_HOOK**, wie in CRTDBG.H definiert:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Wenn die Hookfunktion von der Laufzeitbibliothek aufgerufen wird, enthält das *nRptType*-Argument die Berichtskategorie ( **_CRT_WARN**, **_CRT_ERROR** oder **_CRT_ASSERT**); *szMsg* enthält einen Zeiger auf eine vollständig assemblierte Berichtsmeldungszeichenfolge, und *retVal* gibt an, ob `_CrtDbgReport` nach der Berichtgenerierung die normale Ausführung fortsetzen oder den Debugger starten soll. (Bei einem *retVal*-Wert von 0 (null) wird die Ausführung fortgesetzt, und bei einem Wert von 1 wird der Debugger gestartet.)  
  
 Wenn die betreffende Meldung vollständig vom Hook behandelt wird, sodass kein weiterer Bericht erforderlich ist, muss er **TRUE** zurückgeben. Wenn **FALSE** zurückgegeben wird, gibt `_CrtDbgReport` die Meldung wie üblich aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben von Hookfunktionen für Hook](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, Beispiel](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
