---
title: 'CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte werden Groß-/Kleinschreibung korrekt | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38d8195baa540c2c212c71938b6266e28df49101
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683066"
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
 Eine Ressourcenzeichenfolge enthält ein zusammengesetztes Wort, das anscheinend nicht beachtet werden.

## <a name="rule-description"></a>Regelbeschreibung
 Jedes Wort in der Ressourcenzeichenfolge wird in einzelne Token unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. Beispiele für zusammengesetzte Wörter, die dazu führen, einen Verstoß dass sind "CheckSum" und "MultiPart", die als "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen gängige Nutzungsform einige Ausnahmen werden in der Regel erstellt, und mehrere einzelne Wörter gekennzeichnet sind, z. B. "Toolbar" und "Filename", die als zwei unterschiedliche Wörter Groß-/Kleinschreibung beachtet werden sollten. In diesem Beispiel würde "ToolBar" und "FileName" gekennzeichnet werden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie das Wort, sodass es die richtige Groß-/Kleinschreibung wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn beide Teile der zusammengesetzte Begriff von der Wörterbuch erkannt werden und die Absicht ist, verwenden Sie zwei Wörter.

 Sie können auch ein benutzerdefiniertes Wörterbuch für die Rechtschreibprüfung zusammengesetzte Wörter hinzugefügt. Wörter im benutzerdefinierten Wörterbuchs verursachen keine Verstöße. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Verwandte Regeln
 [CA1702: Bei zusammengesetzten Begriffen sollte beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Siehe auch
 [Großschreibung Konventionen](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [Benennungsrichtlinien](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
