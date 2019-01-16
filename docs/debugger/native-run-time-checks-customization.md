---
title: Systemeigene Laufzeitüberprüfungen Anpassung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7530f875b3eb14766e32b1237871e6ec48d4bb85
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836236"
---
# <a name="native-run-time-checks-customization"></a>Anpassen der systemeigenen Laufzeitüberprüfung
Beim Kompilieren mit **/RTC** (laufzeitfehlerüberprüfungen), oder Verwenden der `runtime_checks` Pragma stellt die C-Laufzeitbibliothek systemeigene laufzeitüberprüfungen bereit. In einigen Fällen können Sie die Laufzeitüberprüfung anpassen:  
  
- Zum Weiterleiten von Meldungen der Laufzeitüberprüfung an eine Datei oder an ein vom Standardziel abweichendes Ziel.  
  
- Zum Festlegen eines Ausgabeziels für Meldungen der Laufzeitüberprüfung im Debugger eines Drittanbieters.  
  
- Zum Erfassen von Meldungen der Laufzeitüberprüfung aus einem Programm, das mit einer Releaseversion der C-Laufzeitbibliothek kompiliert wurde. Releaseversionen der Bibliothek verwenden zum Erfassen von Laufzeitfehlern nicht `_CrtDbgReportW`. Stattdessen wird für jeden Laufzeitfehler ein Dialogfeld **Assert** angezeigt.  
  
  Sie haben folgende Möglichkeiten, um Laufzeitfehlerüberprüfungen anzupassen:  
  
- Schreiben einer Funktion zur Erstellung von Laufzeitfehlerberichten. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Berichtsfunktion für Laufzeitfehler](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Anpassen des Ziels für Fehlermeldungen.  
  
- Abfrage von Informationen zu Laufzeitfehlerüberprüfungen.  
  
## <a name="customize-the-error-message-destination"></a>Anpassen des Ziels für Fehlermeldungen  
 Wenn Sie `_CrtDbgReportW` zum Erfassen von Fehlern verwenden, können Sie das Ziel der Fehlermeldungen mit `_CrtSetReportMode` angeben.  
  
 Wenn Sie mit einer benutzerdefinierten Berichtsfunktion arbeiten, verwenden Sie `_RTC_SetErrorType`, um Fehlern Berichtstypen zuzuordnen.  
  
## <a name="query-for-information-about-run-time-checks"></a>Abfragen von Informationen zu Laufzeitüberprüfungen  
 `_RTC_NumErrors` gibt die Anzahl der Fehlertypen zurück, die bei Laufzeitfehlerüberprüfungen entdeckt wurden. Um eine kurze Beschreibung der einzelnen Fehler zu erhalten, können Sie eine Schleife von 0 bis zum Rückgabewert von `_RTC_NumErrors` durchlaufen, wobei der Iterationswert in jedem Schleifendurchlauf an `_RTC_GetErrDesc` übergeben wird. Weitere Informationen finden Sie unter [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) und [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden von nativen Laufzeitüberprüfungen](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)