---
title: 'CA1701: Ressourcen Zeichenfolgen-Verbund Wörter müssen ordnungsgemäß geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669273"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Ressourcen Zeichenfolge enthält ein zusammengesetztes Wort, das anscheinend nicht ordnungsgemäß geschrieben wird.

## <a name="rule-description"></a>Regelbeschreibung
 Jedes Wort in der Ressourcen Zeichenfolge wird in Token aufgeteilt, die auf der Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. Beispiele für zusammengesetzte Wörter, die zu einer Verletzung führen, sind "Checksum" und "multipart", die als "Checksum" und "multipart" bezeichnet werden müssen. Aufgrund früherer allgemeiner Verwendung sind mehrere Ausnahmen in die Regel integriert, und es werden mehrere einzelne Wörter gekennzeichnet, z. b. "Toolbar" und "filename", die als zwei unterschiedliche Wörter geschrieben werden sollten. In diesem Beispiel würden "Toolbar" und "filename" gekennzeichnet werden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie das Wort, damit es ordnungsgemäß geschrieben wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn beide Teile des Verbund Worts vom Rechtschreib Wörterbuch erkannt werden und die Absicht ist, zwei Wörter zu verwenden.

 Sie können auch Verbund Wörter zu einem Benutzerwörterbuch für die Rechtschreibprüfung hinzufügen. Wörter im benutzerdefinierten Wörterbuch verursachen keine Verstöße. Weitere Informationen finden Sie unter [Vorgehensweise: Passen Sie das Code Analyse-Wörterbuch ](../code-quality/how-to-customize-the-code-analysis-dictionary.md) an.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1702: Zusammengesetzte Wörter sollten korrekt geschrieben werden ](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Bezeichner sollten korrekt geschrieben werden ](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich um mehr als die Groß-/Kleinschreibung unterscheiden

## <a name="see-also"></a>Siehe auch
 [Benennungs Richtlinien](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) für [Benennungs Konventionen](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
