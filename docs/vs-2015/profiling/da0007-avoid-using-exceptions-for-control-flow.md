---
title: 'DA0007: Verwenden Sie keine Ausnahmen für die Ablaufsteuerung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2599282909c62e3a35702346f793dfd914c18ac4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770833"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Verwenden Sie keine Ausnahmen für die Ablaufsteuerung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0007 |  
| Kategorie |. NET Framework-Verwendung |  
| Profilerstellungsmethoden | Alle |  
| Nachricht | Permanent wird eine hohe Anzahl von Ausnahmen ausgelöst. Verwenden Sie nach Möglichkeit weniger Ausnahmen in der Programmlogik.|  
| Nachrichtentyp | Warnung |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 In den Profilerstellungsdaten wurde eine Vielzahl von .NET Framework-Ausnahmehandlern aufgerufen. Verwenden Sie ggf. eine andere Kontrollflusslogik, um die Anzahl der ausgelösten Ausnahmen zu verringern.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Während die Verwendung von Ausnahmehandlern zum Abfangen von Fehlern und anderen Ereignissen, durch die die Programmausführung unterbrochen wird, eine empfohlene Vorgehensweise ist, kann die Verwendung des Ausnahmehandlers als Teil der regulären Programmausführungslogik sehr speicherintensiv sein und sollte vermieden werden. In der Regel sollten Ausnahmen nur für außergewöhnliche und unerwartete Umstände verwendet werden. Ausnahmen sollten nicht verwendet werden, um Werte als Teil des typischen Programmablaufs zurückzugeben. Häufig können Sie das Auslösen von Ausnahmen vermeiden, wenn Sie Werte überprüfen und mithilfe einer bedingten Logik die Ausführung von Anweisungen anhalten, von denen das Problem verursacht wird.  
  
 Weitere Informationen finden Sie im Abschnitt [Exception Management (Ausnahmeverwaltung)](http://go.microsoft.com/fwlink/?LinkID=177825) in **Chapter 5 – Improving Managed Code Performance (Kapitel 5 – Verbessern der Leistung von verwaltetem Code)** im Band **Improving .NET Application Performance and Scalability (Verbessern von Leistung und Skalierbarkeit von .NET-Anwendungen)** der Microsoft-Bibliothek für **Muster und Vorgehensweisen** im MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht „Markierungen“ zu navigieren. Suchen Sie die Spalte, die die Messung für **.NET CLR-Ausnahmen(@ProcessInstance)\\Anzahl der ausgelösten Ausnahmen/Sek.** enthält. Überprüfen Sie, ob die Ausnahmebehandlung in bestimmten Phasen der Programmausführung besonders häufig auftritt. Suchen Sie mithilfe eines Samplingprofils nach throw-Anweisungen und try/catch-Blöcken, die häufig Ausnahmen generieren. Ergänzen Sie ggf. catch-Blöcke mit einer Logik, die zeigt, welche Ausnahmen am häufigsten behandelt werden. Ersetzen Sie nach Möglichkeit häufig ausgeführte throw-Anweisungen oder catch-Blöcke durch einfache Flusssteuerungslogik oder Validierungscode.  
  
 Wenn Sie beispielsweise feststellen, dass von Ihrer Anwendung häufig DivideByZeroException-Ausnahmen behandelt werden, können Sie die Leistung der Anwendung verbessern, indem Sie eine Logik zum Programm hinzuzufügen, mit der überprüft wird, ob Nenner mit dem Wert null vorhanden sind.
