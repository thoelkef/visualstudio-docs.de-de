---
title: 'CA1702: Zusammengesetzte Wörter müssen ordnungsgemäß geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 76ce346430a249b562f00e17c3173e79128d1708
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669257"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1702: Zusammengesetzte Wörter sollten ](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) ordnungsgemäß geschrieben werden.

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: Wenn Assemblys ausgelöst werden.<br /><br /> Nicht unterbrechend: Wenn für Typparameter ausgelöst wird.|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners enthält mehrere Wörter, und mindestens eines der Wörter erscheint als zusammengesetztes Wort, das nicht ordnungsgemäß geschrieben ist.

## <a name="rule-description"></a>Regelbeschreibung
 Der Name des Bezeichners wird in Wörter aufgeteilt, die auf der Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Wörtern wird von der Bibliothek der Microsoft-Rechtschreibprüfung überprüft. Wenn es erkannt wird, führt der Bezeichner zu einem Verstoß gegen die Regel. Beispiele für zusammengesetzte Wörter, die zu einer Verletzung führen, sind "Checksum" und "multipart", die als "Checksum" und "multipart" bezeichnet werden müssen. Aufgrund früherer allgemeiner Verwendung sind mehrere Ausnahmen in die Regel integriert, und es werden mehrere einzelne Wörter gekennzeichnet, z. b. "Toolbar" und "filename", die als zwei unterschiedliche Wörter (in diesem Fall "Toolbar" und "filename") geschrieben werden sollten.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen so, dass er richtig geschrieben ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn beide Teile des Verbund Worts vom Rechtschreib Wörterbuch erkannt werden und die Absicht ist, zwei Wörter zu verwenden.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1701: Ressourcen Zeichenfolgen-Verbund Wörter müssen ordnungsgemäß geschrieben werden ](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Bezeichner sollten korrekt geschrieben werden ](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich um mehr als die Groß-/Kleinschreibung unterscheiden

## <a name="see-also"></a>Siehe auch
 [Benennungs Richtlinien](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) für [Benennungs Richtlinien](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
