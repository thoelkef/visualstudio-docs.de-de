---
title: "DA0006: Equals() f&#252;r Werttypen &#252;berschreiben | Microsoft Docs"
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
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006: Equals() f&#252;r Werttypen &#252;berschreiben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0006|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling|  
|Meldung|Equals und Gleichheitsoperator in Werttypen überschreiben|  
|Meldungstyp|Warnung|  
  
## Ursache  
 Aufrufe der Equals\-Methode oder der Gleichheitsoperatoren eines öffentlichen Werttyps machen einen großen Teil der Profilerstellungsdaten aus.  Implementieren Sie ggf. eine effizientere Methode.  
  
## Regelbeschreibung  
 Bei Werttypen wird die <xref:System.Reflection>\-Bibliothek von der geerbten Implementierung von Equals verwendet, und der Inhalt aller Felder wird verglichen.  Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig.  Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie diese als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren.  Wenn die Programmiersprache das Überladen von Operatoren unterstützt, sollten Sie außerdem eine Implementierung der Gleichheits\- und Ungleichheitsoperatoren bereitstellen.  
  
 Weitere Informationen dazu, wie und Equals der Gleichheitsoperatoren, finden Sie überschreibt [Richtlinien für die Implementierung von Equals verwendet und der Gleichheitsoperator \(\=\=\)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Ein Beispiel zum Implementieren der Equals\- und Gleichheitsoperatoren finden Sie in der Codeanalyseregel [CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md).