---
title: "CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9332359228d657e9155996443822a5d1c11ad01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn auf Assemblys, Namespaces, Typen, Member und Parameter ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für generische Typparameter ausgelöst.|  
  
## <a name="cause"></a>Ursache  
 Der Name eines Bezeichners ist nicht ordnungsgemäß Groß-/Kleinschreibung beachtet.  
  
 \- oder –  
  
 Der Name eines Bezeichners enthält eine zweibuchstabige Abkürzung, und der zweite Buchstabe ist Kleinbuchstaben.  
  
 \- oder –  
  
 Der Name eines Bezeichners enthält ein Akronym mindestens drei Großbuchstaben.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
 Verwenden Sie gemäß der Konvention werden Parameternamen Kamel-Schreibweise; Namespace, Typ-und Membernamen verwenden Pascal Schreibweise. In einem Namen in Kamel-Schreibweise der erste Buchstabe Kleinbuchstaben ist, und der erste Buchstabe des verbleibenden Wörter im Namen besteht aus Großbuchstaben. Beispiele für Namen in Kamel-Schreibweise sind "PacketSniffer", "IoFile" und "FatalErrorCode". In einem Namen Pascal-Schreibweise angegeben der erste Buchstabe ein Großbuchstabe ist, und der erste Buchstabe des verbleibenden Wörter im Namen besteht aus Großbuchstaben. Beispiele für Namen Pascal-Schreibweise sind "PacketSniffer", "IOFile" und "FatalErrorCode".  
  
 Diese Regel teilt den Namen in Wörter, die basierend auf die Groß-/Kleinschreibung und überprüft alle zweistelliger Wörter mit einer Liste der allgemeinen zweibuchstabige Wörter wie "In" oder "My". Wenn eine Übereinstimmung gefunden wird, wird davon ausgegangen, dass das Wort ein Akronym werden. Mit dieser Regel wird außerdem davon ausgegangen, dass es ein Akronym gefunden hat, wenn der Name entweder vier Großbuchstaben in einer Zeile oder drei Großbuchstaben in einer Zeile am Ende des Namens enthält.  
  
 Gemäß der Konvention zweibuchstabige Akronyme verwenden alle Großbuchstaben und Akronymen mit drei oder mehr Zeichen Pascal Schreibweise. Die folgenden Beispiele verwenden diese Namenskonvention: "DB", "CR", "Cpa" und "Ecma". In den folgenden Beispielen verstoßen gegen die Konvention: "-e/a", "XML" und "DoD" sowie zum Nonparameter Namen, "Xp" und "Systemsteuerungsoption".  
  
 "ID" ist, einen Sonderfall dar, die dazu führen, dass einen Verstoß gegen diese Regel. "Id" ist ein Akronym, aber es ist eine Abkürzung für "ID".  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie den Namen, damit es ordnungsgemäß Groß-/Kleinschreibung beachtet wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf diese Warnung zu unterdrücken, wenn Sie Ihre eigenen Benennungskonventionen haben oder der Bezeichner Eigennamen, beispielsweise den Namen des Unternehmens oder einer Technologie darstellt.  
  
 Sie können auch bestimmte Begriffe und Abkürzungen Akronyme hinzufügen, um eine benutzerdefinierte Codeanalysewörterbuchs. In der Benutzerwörterbuch angegebenen Begriffe verursacht keine Verstöße gegen diese Regel. Weitere Informationen finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)