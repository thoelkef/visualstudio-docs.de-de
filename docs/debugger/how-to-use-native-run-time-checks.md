---
title: "Gewusst wie: Verwenden von systemeigenen Laufzeitpr&#252;fungen | Microsoft Docs"
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
  - "c.runtime.errorchecks"
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
  - "/O (Compileroption), /RTC-Option"
  - "/RTC-Compileroption [C++], /O (Compileroption)"
  - "Arrays [Visual Basic], Debuggen"
  - "Debugger, Systemeigene Laufzeitüberprüfungen"
  - "Debugger, Laufzeitfehler"
  - "Debuggen von Arrays"
  - "Systemeigene Laufzeitüberprüfungen"
  - "O (Compileroption), /RTC-Option"
  - "Optimierte Buildoption"
  - "RTC-Compileroption, /O (Compileroption)"
  - "Laufzeitüberprüfungen"
  - "Laufzeitüberprüfungen, Systemeigen"
  - "Laufzeitfehler, Debuggen"
  - "Laufzeitfehler, Fehlerüberprüfung"
  - "runtime_checks-Pragma"
  - "Stapelzeiger"
  - "Stapelzeiger, Beschädigung"
  - "Stapel, Zeigerbeschädigung"
  - "Variablen [Debugger], Abfangen von Abhängigkeiten von nicht initialisierten lokalen Variablen"
  - "Variablen [Debugger], Verlust von Daten"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden von systemeigenen Laufzeitpr&#252;fungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual C\+\+ können Sie mit systemeigenen [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) häufige Laufzeitfehler abfangen. Beispiele:  
  
-   Beschädigung des Stapelzeigers  
  
-   Überläufe lokaler Arrays  
  
-   Beschädigung des Stapels  
  
-   Abhängigkeiten von nicht initialisierten lokalen Variablen  
  
-   Datenverlust nach einer Zuordnung zu einer kürzeren Variablen  
  
 Wenn Sie **\/RTC** mit einem optimierten \(**\/O**\) Build verwenden, wird ein Compilerfehler ausgelöst. Wenn Sie in einem optimierten Build ein `runtime_checks`\-Pragma verwenden, hat das Pragma keine Auswirkungen.  
  
 Wenn Sie ein Programm mit aktivierten Laufzeitüberprüfungen debuggen, wird das Programm beim Auftreten eines Laufzeitfehlers standardmäßig unterbrochen und wechselt in den Debugger. Sie können dieses Standardverhalten für jede Laufzeitüberprüfung ändern. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 In den folgenden Prozeduren wird beschrieben, wie Sie in einem Debugbuild systemeigene Laufzeitüberprüfungen aktivieren und das Verhalten systemeigener Laufzeitüberprüfungen ändern.  
  
 Weitere Themen in diesem Abschnitt enthalten Informationen zu folgenden Vorgängen:  
  
-   [Anpassen von Laufzeitüberprüfungen mit der C\-Laufzeitbibliothek](../debugger/native-run-time-checks-customization.md)  
  
-   [Verwenden von Laufzeitüberprüfungen ohne die C\-Laufzeitbibliothek](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### So aktivieren Sie systemeigene Laufzeitfehlerüberprüfungen in einem Debugbuild  
  
-   Verwenden Sie die Option **\/RTC**, und stellen Sie eine Verknüpfung zu der Debugversion einer C\-Laufzeitbibliothek \(z. B. \/MDd\) her.  
  
### So ändern Sie das Verhalten von systemeigenen Laufzeitfehlerüberprüfungen  
  
-   Verwenden Sie das `runtime_checks`\-Pragma.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [Laufzeitfehlerüberprüfung](/visual-cpp/c-runtime-library/run-time-error-checking)