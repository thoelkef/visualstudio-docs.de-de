---
title: 'CA1709: Bezeichner sollten werden Groß-/Kleinschreibung korrekt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a06d85367ae40b05e76f89c9b1bf0dac11e1980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511016"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung korrekt](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) auf docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Wichtige – Wenn auf Assemblys, Namespaces, Typen, Member und Parameter ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für den generischen Parameter des Typs ausgelöst.|  
  
## <a name="cause"></a>Ursache  
 Der Name eines Bezeichners ist keine korrekte Groß-/Kleinschreibung.  
  
 \- oder –  
  
 Der Name eines Bezeichners enthält eine zweibuchstabige Abkürzung, und ist der zweite Buchstaben in Kleinbuchstaben.  
  
 \- oder –  
  
 Der Name eines Bezeichners enthält ein Akronym mindestens drei Großbuchstaben.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
 Gemäß der Konvention wird Kamel-Schreibweise von Parameternamen verwenden; Namespace, Typ und Membername Pascal-Schreibweise verwendet zur Groß-und Kleinschreibung. In einem Namen in Kamel-Schreibweise ist der erste Buchstaben in Kleinbuchstaben, und die erste Buchstaben des verbleibenden Wörter im Namen ist in Großbuchstaben. Beispiele für Camel-Case-Namen sind "PacketSniffer", "IoFile" und "FatalErrorCode". In einem Namen Pascal-Schreibweise verwendet der erste Buchstaben wird Groß- und der erste Buchstaben des verbleibenden Wörter im Namen ist in Großbuchstaben. Beispiele für Namen Pascal-Schreibweise angegeben sind "PacketSniffer", "IOFile" und "FatalErrorCode".  
  
 Diese Regel den Namen in Wörter, die basierend auf die Groß-/Kleinschreibung unterteilt und überprüft alle zwei Buchstaben bestehenden Wörter mit einer Liste der allgemeinen zwei Buchstaben bestehenden Wörter wie "In" oder "My". Wenn eine Übereinstimmung nicht gefunden wird, wird angenommen, dass das Wort ein Akronym handelt. Mit dieser Regel wird außerdem davon ausgegangen, dass es ein Akronym gefunden hat, wenn Sie den Namen entweder vier Großbuchstaben in einer Zeile oder drei Großbuchstaben in einer Zeile am Ende des Namens enthält.  
  
 Gemäß der Konvention verwenden zwei Buchstaben bestehenden Akronyme Großbuchstaben und Akronyme der drei oder mehr Zeichen verwenden Pascal-Schreibweise zur Groß-und Kleinschreibung. Die folgenden Beispiele verwenden die Benennungskonvention: "DB", "CR", "Cpa" und "Ecma". In den folgenden Beispielen verstoßen gegen die Konvention: '-e/a', 'XML' und "DoD", und für Nonparameter Namen, "Xp" und "cpl".  
  
 "ID" ist, einen Sonderfall dar, die dazu führen, dass einen Verstoß gegen diese Regel. "Id" ist kein Akronym, aber es ist eine Abkürzung für "ID".  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie den Namen, damit sie die richtige Groß-/Kleinschreibung ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Es ist sicher, diese Warnung zu unterdrücken, wenn Sie Ihre eigenen Benennungskonventionen haben oder wenn der Bezeichner, einen ordnungsgemäßen Namen, z. B. den Namen eines Unternehmens oder eine Technologie darstellt.  
  
 Sie können auch bestimmte Begriffe, Abkürzungen und Akronyme hinzufügen, um ein benutzerdefiniertes Wörterbuch des Code-Analyse. In benutzerdefinierten Wörterbuchs angegebenen Begriffe verursacht keine Verstöße gegen diese Regel. Weitere Informationen finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

