---
title: "CA1709: Bei Bezeichnern sollte die Gro&#223;-/Kleinschreibung beachtet werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1709: Bei Bezeichnern sollte die Gro&#223;-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys, Namespaces, Typen, Member und Parameter ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für generische Typparameter ausgelöst.|  
  
## Ursache  
 Der Name eines Bezeichners verfügt nicht über die richtige Groß\-\/Kleinschreibung.  
  
 – oder –  
  
 Der Name eines Bezeichners enthält ein Akronym aus zwei Buchstaben, und der zweite Buchstabe ist kleingeschrieben.  
  
 – oder –  
  
 Der Name eines Bezeichners enthält ein Akronym mit drei oder mehr Großbuchstaben.  
  
## Regelbeschreibung  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
 Gemäß der Konvention werden Parameternamen in Kamel\-Schreibweise verfasst. Für Namespace\-, Typ\- und Membernamen wird die Pascal\-Schreibweise verwendet.  In Namen in Kamel\-Schreibweise ist der erste Buchstabe ein Kleinbuchstabe, und jedes weitere Wort im Namen fängt mit einem Großbuchstaben an.  Beispiele für Namen in Kamel\-Schreibweise sind "packetSniffer", "ioFile" und "fatalErrorCode".  In Namen in der Pascal\-Schreibweise ist der erste Buchstabe ein Großbuchstabe, und jedes weitere Wort im Namen fängt mit einem Großbuchstaben an.  Beispiele für Namen in Pascal\-Schreibweise sind "PacketSniffer", "IOFile" und "FatalErrorCode".  
  
 Während der Überprüfung dieser Regel wird der Name auf der Grundlage der Groß\-\/Kleinschreibung in Wörter aufgeteilt, und alle aus zwei Buchstaben bestehenden Wörter werden mit einer Liste häufig gebrauchter Wörter, die aus zwei Buchstaben bestehen, verglichen, z. B. "In" oder "My".  Wird keine Übereinstimmung gefunden, wird angenommen, dass es sich bei dem Wort um ein Akronym handelt.  Bei dieser Regel wird davon ausgegangen, dass ein Akronym gefunden wurde, wenn der Name vier Großbuchstaben nacheinander bzw. am Ende des Namens drei Großbuchstaben nacheinander enthält.  
  
 Aus zwei Buchstaben bestehende Akronyme umfassen in der Regel nur Großbuchstaben, bei Akronymen mit drei oder mehr Zeichen wird die Pascal\-Schreibweise verwendet.  Die folgenden Beispiele verwenden diese Namenskonvention: "DB", "CR", "Cpa" und "Ecma".  Die folgenden Beispiele verstoßen gegen die Konvention: "Io", "XML" und "DoD" sowie "xp" und "cpl" für Namen, bei denen es sich nicht um Parameternamen handelt.  
  
 "ID" weist eine spezielle Schreibweise auf, um einen Verstoß gegen diese Regel zu verursachen. "IDs" ist, kein Akronym sondern ist eine Abkürzung für "Bezeichner".  
  
## Behandeln von Verstößen  
 Ändern Sie den Namen, sodass er die ordnungsgemäße Groß\-\/Kleinschreibung aufweist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sie können diese Warnung gefahrlos unterdrücken, wenn Sie eigene Namenskonventionen verwenden oder wenn der Bezeichner einen Eigennamen darstellt, z. B. den Namen eines Unternehmens oder einer Technologie.  
  
 Sie können auch bestimmte Begriffe, Abkürzungen und Akronyme zu einem Benutzerwörterbuch für die Codeanalyse hinzufügen.  Im Benutzerwörterbuch angegebene Begriffe verursachen keine Verletzungen dieser Regel.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## Verwandte Regeln  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)