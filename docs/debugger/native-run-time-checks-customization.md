---
title: "Systemeigene Laufzeitüberprüfungen Anpassung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9483983b6cbd5644827af8f647425cce61502ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="native-run-time-checks-customization"></a>Anpassen der systemeigenen Laufzeitüberprüfung
Beim Kompilieren mit **/RTC** (laufzeitfehlerüberprüfungen), oder verwenden Sie die `runtime_checks` Pragma stellt die C-Laufzeitbibliothek systemeigene laufzeitüberprüfungen bereit. In einigen Fällen können Sie die Laufzeitüberprüfung anpassen:  
  
-   Zum Weiterleiten von Meldungen der Laufzeitüberprüfung an eine Datei oder an ein vom Standardziel abweichendes Ziel.  
  
-   Zum Festlegen eines Ausgabeziels für Meldungen der Laufzeitüberprüfung im Debugger eines Drittanbieters.  
  
-   Zum Erfassen von Meldungen der Laufzeitüberprüfung aus einem Programm, das mit einer Releaseversion der C-Laufzeitbibliothek kompiliert wurde. Releaseversionen der Bibliothek verwenden zum Erfassen von Laufzeitfehlern nicht `_CrtDbgReportW`. Stattdessen zeigen sie eine **Assert** für jeden Laufzeitfehler im Dialogfeld.  
  
 Sie haben folgende Möglichkeiten, um Laufzeitfehlerüberprüfungen anzupassen:  
  
-   Schreiben einer Funktion zur Erstellung von Laufzeitfehlerberichten. Weitere Informationen finden Sie unter [wie: Schreiben einer Run-Time Error Reporting-Funktion](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Anpassen des Ziels für Fehlermeldungen.  
  
-   Abfrage von Informationen zu Laufzeitfehlerüberprüfungen.  
  
## <a name="customize-the-error-message-destination"></a>Anpassen des Ziels für Fehlermeldungen  
 Wenn Sie `_CrtDbgReportW` zum Erfassen von Fehlern verwenden, können Sie das Ziel der Fehlermeldungen mit `_CrtSetReportMode` angeben.  
  
 Wenn Sie mit einer benutzerdefinierten Berichtsfunktion arbeiten, verwenden Sie `_RTC_SetErrorType`, um Fehlern Berichtstypen zuzuordnen.  
  
## <a name="query-for-information-about-run-time-checks"></a>Abfragen von Informationen zu Laufzeitüberprüfungen  
 `_RTC_NumErrors` gibt die Anzahl der Fehlertypen zurück, die bei Laufzeitfehlerüberprüfungen entdeckt wurden. Um eine kurze Beschreibung der einzelnen Fehler zu erhalten, können Sie eine Schleife von 0 bis zum Rückgabewert von `_RTC_NumErrors` durchlaufen, wobei der Iterationswert in jedem Schleifendurchlauf an `_RTC_GetErrDesc` übergeben wird. Weitere Informationen finden Sie unter [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) und [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden von systemeigenen Laufzeitfehlerüberprüfungen](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)