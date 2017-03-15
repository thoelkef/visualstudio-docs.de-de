---
title: "DA0007: Verwenden Sie keine Ausnahmen f&#252;r die Ablaufsteuerung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0007: Verwenden Sie keine Ausnahmen f&#252;r die Ablaufsteuerung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0007|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Alle|  
|Meldung|Es wird permanent eine hohe Anzahl von Ausnahmen ausgelöst.  Verwenden Sie nach Möglichkeit weniger Ausnahmen in der Programmlogik.|  
|Meldungstyp|Warnung|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 In den Profilerstellungsdaten wurde eine Vielzahl von .NET Framework\-Ausnahmehandlern aufgerufen.  Verwenden Sie ggf. eine andere Kontrollflusslogik, um die Anzahl der ausgelösten Ausnahmen zu verringern.  
  
## Regelbeschreibung  
 Während die Verwendung von Ausnahmehandlern, um Fehler und andere Ereignisse abzufangen, die die Programmausführung unterbrechen, eine empfohlene Vorgehensweise ist, kann die Verwendung des Ausnahmehandlers als Teil der regulären Programmausführungslogik aufwendig sein und sollte vermieden werden.  In der Regel sollten Ausnahmen nur für außergewöhnliche und unerwartete Umstände verwendet werden.  Ausnahmen sollten nicht verwendet werden, um Werte als Teil des typischen Programmablaufs zurückzugeben.  In vielen Fällen können Sie vermeiden, Ausnahmen auszulösen, indem Sie Werte überprüfen und mithilfe bedingter Logik die Ausführung von Anweisungen anhalten, die das Problem verursachen.  
  
 Weitere Informationen finden Sie im [Ausnahme\-Verwaltung](http://go.microsoft.com/fwlink/?LinkID=177825)\-Abschnitt von **Chapter 5 — Improving Managed Code Performance** im **Improving .NET Application Performance and ScalabilityMicrosoft Patterns and Practices** der Lautstärke Bibliothek auf MSDN.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie im Fenster "Fehlerliste" auf die Meldung, um zur Ansicht Markierungen zu navigieren.  Suchen Sie die Spalte, die die **.NET\-CLR\-Ausnahmen \(@ProcessInstance\)\\Anzahl der ausgelösten Ausnahmen\/Sek.** enthält.  Überprüfen Sie, ob die Ausnahmebehandlung in bestimmten Phasen der Programmausführung besonders häufig ausfällt.  Versuchen Sie mit einem Samplingprofil, throw\-Anweisungen und try\/catch\-Blöcke zu identifizieren, die häufige Ausnahmen generieren.  Falls notwendig, fügen Sie catch\-Blöcken Logik hinzu, die zeigt, welche Ausnahmen am häufigsten behandelt werden.  Ersetzen Sie nach Möglichkeit häufig ausgeführte throw\-Anweisungen oder catch\-Blöcke durch einfache Flusssteuerungslogik oder Validierungscode.  
  
 Wenn Sie zum Beispiel finden sollten, dass die Anwendung häufige DivideByZeroException\-Ausnahmen behandelt hat, verbessert es die Leistung der Anwendung, wenn Sie eine Logik zum Programm hinzuzufügen, die Nenner mit Wert 0 \(null\) überprüft.