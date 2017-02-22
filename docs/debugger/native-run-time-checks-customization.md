---
title: "Anpassen der systemeigenen Laufzeit&#252;berpr&#252;fung | Microsoft Docs"
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
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/RTC-Compileroption [C++], Systemeigene Laufzeitüberprüfungen"
  - "Anpassen der CRT-Fehlerüberprüfung"
  - "Debugger, Systemeigene Laufzeitüberprüfungen"
  - "Systemeigene Laufzeitüberprüfungen, Anpassen"
  - "runtime_checks-Pragma"
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anpassen der systemeigenen Laufzeit&#252;berpr&#252;fung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei der Kompilierung mit **\/RTC** \(Run\-Time Checks, Laufzeitüberprüfungen\) oder mit dem `runtime_checks`\-Pragma stellt die C\-Laufzeitbibliothek systemeigene Laufzeitüberprüfungen zur Verfügung.  In einigen Fällen können Sie die Laufzeitüberprüfung anpassen:  
  
-   Zum Weiterleiten von Meldungen der Laufzeitüberprüfung an eine Datei oder an ein vom Standardziel abweichendes Ziel.  
  
-   Zum Festlegen eines Ausgabeziels für Meldungen der Laufzeitüberprüfung im Debugger eines Drittanbieters.  
  
-   Zum Erfassen von Meldungen der Laufzeitüberprüfung aus einem Programm, das mit einer Releaseversion der C\-Laufzeitbibliothek kompiliert wurde.  Releaseversionen der Bibliothek verwenden zum Erfassen von Laufzeitfehlern nicht `_CrtDbgReportW`.  Stattdessen wird für jeden Laufzeitfehler ein Dialogfeld **Assert** angezeigt.  
  
 Sie haben folgende Möglichkeiten, um Laufzeitfehlerüberprüfungen anzupassen:  
  
-   Schreiben einer Funktion zur Erstellung von Laufzeitfehlerberichten.  Weitere Informationen finden Sie unter [Gewusst wie: Schreiben einer Berichtsfunktion für Laufzeitfehler](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Anpassen des Ziels für Fehlermeldungen.  
  
-   Abfrage von Informationen zu Laufzeitfehlerüberprüfungen.  
  
## Anpassen des Ziels für Fehlermeldungen  
 Wenn Sie `_CrtDbgReportW` zum Erfassen von Fehlern verwenden, können Sie das Ziel der Fehlermeldungen mit `_CrtSetReportMode` angeben.  
  
 Wenn Sie mit einer benutzerdefinierten Berichtsfunktion arbeiten, verwenden Sie `_RTC_SetErrorType`, um Fehlern Berichtstypen zuzuordnen.  
  
## Abfragen von Informationen zu Laufzeitüberprüfungen  
 `_RTC_NumErrors` gibt die Anzahl der Fehlertypen zurück, die bei Laufzeitfehlerüberprüfungen entdeckt wurden.  Um eine kurze Beschreibung der einzelnen Fehler zu erhalten, können Sie eine Schleife von 0 bis zum Rückgabewert von `_RTC_NumErrors` durchlaufen, wobei der Iterationswert in jedem Schleifendurchlauf an `_RTC_GetErrDesc` übergeben wird.  Weitere Informationen finden Sie unter [\_RTC\_NumErrors](/visual-cpp/c-runtime-library/reference/rtc-numerrors) und unter [\_RTC\_GetErrDesc](/visual-cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## Siehe auch  
 [Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [\_CrtDbgReport, \_CrtDbgReportW](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)