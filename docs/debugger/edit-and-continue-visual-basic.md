---
title: "Bearbeiten und Fortfahren (Visual&#160;Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "64 Bit (Bearbeiten und Fortfahren)"
  - "Debuggen [Visual Basic], Bearbeiten und Fortfahren"
  - "Bearbeiten und Fortfahren [Visual Basic]"
  - "Bearbeiten und Fortfahren, 64 Bit"
  - "Visual Basic, Bearbeiten und Fortfahren"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# Bearbeiten und Fortfahren (Visual&#160;Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bearbeiten und Fortfahren ist ein Feature von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Debuggen, mit dem Sie den Code ändern können, während der Unterbrechungsmodus ausgeführt wird.  Nachdem Codebearbeitungen übernommen wurden, können Sie die Ausführung mit den neuen Änderungen fortsetzen und deren Auswirkung beobachten.  
  
 Sie können das Feature Bearbeiten und Fortfahren immer dann verwenden, wenn Sie sich im Unterbrechungsmodus befinden.  Im Unterbrechungsmodus zeigt der Anweisungszeiger \(eine gelbe Pfeilspitze im Quellcodefenster\) auf die Zeile, die als nächste Zeile ausgeführt wird. Er wird auf eine ausführbare Anweisung innerhalb eines Methodentexts oder eines Eigenschaftentexts positioniert.  Im Unterbrechungsmodus kann an einer ausführbaren Anweisung nahezu jede Änderung vorgenommen werden. Die vorgenommene Änderung wird im zugrunde liegenden Projekt übernommen.  Allerdings ist es im Unterbrechungsmodus im Allgemeinen nicht zulässig, Deklarationsanweisungen, wie öffentliche Methoden, öffentliche Felder oder Klassendeklarationen, zu ändern.  
  
 Wenn Sie eine unberechtigte Bearbeitung vornehmen, wird die Änderung durch eine violette wellenförmige Linie gekennzeichnet, und in der Aufgabenliste wird eine Aufgabe angezeigt.  Sie müssen eine unberechtigte Bearbeitung rückgängig machen, wenn Sie Bearbeiten und Fortfahren weiterhin verwenden möchten.  Bestimmte unberechtigte Bearbeitungen sind möglicherweise zulässig, wenn sie außerhalb von Bearbeiten und Fortfahren durchgeführt werden.  Wenn Sie die Ergebnisse einer solchen unberechtigten Bearbeitung beibehalten möchten, müssen Sie das Debuggen beenden und die Anwendung neu starten.  
  
 Die Funktion "Bearbeiten und Fortfahren" wird für 64\-Bit\-Projekte unterstützt, die auf .NET Framework 4.5.1 abzielen.  
  
 Bearbeiten und Fortfahren wird nicht unterstützt, wenn Sie das Debuggen mit **An den Prozess anhängen** beginnen.  Die Funktion "Bearbeiten und Fortfahren" wird für Projekte mit optimiertem Code, Projekte mit gemischtem verwaltetem und systemeigenem Code sowie für Compact Framework\-Projekte \(intelligente Geräte\) nicht unterstützt.  
  
 In den Themen zu diesem Abschnitt finden Sie weitere Informationen darüber, wie dieses Feature verwendet wird, und welche Arten von Änderungen nicht zulässig sind.  
  
## In diesem Abschnitt  
 [Gewusst wie: Anwenden von Bearbeitungen im Unterbrechungsmodus mithilfe von "Bearbeiten und Fortfahren"](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Erläutert, wie Codebearbeitungen im Unterbrechungsmodus vorgenommen werden.  
  
 [Nicht unterstützte Bearbeitungen beim Bearbeiten und Fortsetzen in Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Hier wird beschrieben, welche Arten von Bearbeitungen nicht mit der Funktion "Bearbeiten und Fortfahren" in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] ausgeführt werden können.  
  
## Verwandte Abschnitte  
 ["Bearbeiten und Fortfahren"](../debugger/edit-and-continue.md)  
 Enthält eine Liste mit Themen zu Bearbeiten und Fortfahren.