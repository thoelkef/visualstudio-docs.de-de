---
title: Unterstützte Codeänderungen (c#) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d028c35ea5d0f00dd8206fbfe0b086c9dbed067
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724661"
---
# <a name="supported-code-changes-c"></a>Unterstützte Codeänderungen (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Funktion "Bearbeiten und Fortfahren" behandelt die meisten Arten von Codeänderungen in Methodentexten. Die meisten Änderungen außerhalb von Methodentexten sowie einige Änderungen in Methodentexten können jedoch während des Debuggens nicht übernommen werden. Wenn Sie diese nicht unterstützten Änderungen übernehmen möchten, müssen Sie das Debuggen beenden und mit einer neuen Version des Codes erneut starten.  
  
 Folgende Änderungen am C#-Code können während einer Debugsitzung nicht übernommen werden:  
  
-   Änderungen an der aktuellen Anweisung oder einer beliebigen anderen aktiven Anweisung.  
  
     Aktive Anweisungen umfassen alle Anweisungen in Funktionen der Aufrufliste, die aufgerufen wurden, um zur aktuellen Anweisung zu gelangen.  
  
     Die aktuelle Anweisung wird im Quellcodefenster durch einen gelben Hintergrund gekennzeichnet. Andere aktive Anweisungen werden durch einen schattierten Hintergrund gekennzeichnet und sind schreibgeschützt. Diese Standardfarben können geändert werden, der **Optionen** Dialogfeld.  
  
-   Ändern der Signatur eines Typs.  
  
-   Hinzufügen einer anonymen Methode, die eine bisher noch nicht erfasste Variable erfasst.  
  
-   Hinzufügen, Entfernen oder Ändern von Attributen.  
  
-   Hinzufügen, Entfernen oder Ändern von `using`-Anweisungen.  
  
-   Hinzufügen von `foreach`, `using` oder `lock` zu der aktiven Anweisung.  
  
## <a name="unsafe-code"></a>Unsicherer Code  
 Bei Änderungen an unsicherem Code gibt es dieselben Einschränkungen wie bei Änderungen an sicherem Code, es gibt jedoch eine zusätzliche Einschränkung: „Bearbeiten und Fortfahren“ unterstützt keine Änderungen an unsicherem Code, der in einer Methode vorhanden ist, die den Operator `stackalloc` enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 „Bearbeiten und Fortfahren“ unterstützt Änderungen an `catch`- und `finally`-Blöcken, und zwar mit der Ausnahme, dass das Hinzufügen eines `catch`- oder `finally`-Blocks um die aktive Anweisung herum nicht zulässig ist.  
  
## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien  
 Bearbeiten und Fortfahren steht in den folgenden Debugszenarios nicht zur Verfügung:  
  
-   Debuggen von LINQ-Code unter bestimmten Umständen. Weitere Informationen finden Sie unter [Debuggen von LINQ](../debugger/debugging-linq.md).  
  
    -   Erfassen einer zuvor noch nicht erfassten Variablen.  
  
    -   Ändern des Typs des Abfrageausdrucks (beispielsweise Auswahl eines =>-Ausdrucks, Auswahl eines neuen Ausdrucks { A = a };)  
  
    -   Entfernen einer `where`-Klausel, die eine aktive Anweisung enthält.  
  
    -   Entfernen einer `let`-Klausel, die eine aktive Anweisung enthält.  
  
    -   Entfernen einer `join`-Klausel, die eine aktive Anweisung enthält.  
  
    -   Entfernen einer `orderby`-Klausel, die eine aktive Anweisung enthält.  
  
-   Debuggen im gemischten Modus (systemeigen/verwaltet).  
  
-   SQL-Debuggen.  
  
-   Debuggen eines Dr.Watson-Dumps.  
  
-   Bearbeiten von Code nach einem Ausnahmefehler, wenn die "**Aufrufliste für Ausnahmefehler entladen**" nicht ausgewählt ist.  
  
-   Debuggen einer eingebetteten Laufzeitanwendung.  
  
-   Debuggen einer Anwendung, die **Anfügen an** anstatt die Anwendung dazu **starten** aus der **Debuggen** Menü.  
  
-   Debuggen von optimiertem Code.  
  
-   Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten Sie und fortfahren Sie (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Gewusst wie: Verwenden von "Bearbeiten und Fortfahren" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)



