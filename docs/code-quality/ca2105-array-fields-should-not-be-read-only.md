---
title: 'CA2105: Arrayfelder dürfen nicht schreibgeschützt sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f8a02ae357dbf36cb4d3e4bd21aaad0fed3a320
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586574"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Arrayfelder dürfen nicht schreibgeschützt sein.

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein öffentliches oder geschütztes Feld, das ein Array enthält, ist schreibgeschützt deklariert.

## <a name="rule-description"></a>Regelbeschreibung

Beim Anwenden der `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Modifizierer, um ein Feld, das ein, das Feld Array kann nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. Code, der Entscheidungen trifft oder führt Vorgänge, die für die Elemente eines Arrays von nur-Lese basieren, die öffentlich zugegriffen werden kann, kann ein ausnutzbaren Sicherheitsrisiko enthalten.

Beachten Sie, dass ein öffentliches Feld mit verstößt auch gegen die Entwurfsregel [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um das Sicherheitsrisiko zu beheben, das von dieser Regel identifiziert wird, verlassen Sie sich nicht auf dem Inhalt eines nur-Lese Arrays, die öffentlich zugegriffen werden kann. Es wird dringend empfohlen, dass Sie eine der folgenden Verfahren verwenden:

- Ersetzen Sie das Array, durch eine stark typisierte Auflistung, die nicht geändert werden kann. Weitere Informationen finden Sie unter <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Ersetzen Sie das öffentliche Feld mit einer Methode, die einen Klon der ein privates Array zurückgibt. Da Ihr Code nicht auf dem Klon abhängig ist, besteht keine Gefahr, wenn die Elemente geändert werden.

Wenn Sie den zweiten Ansatz gewählt haben, ersetzen Sie das Feld nicht mit einer Eigenschaft. Eigenschaften, die Arrays zurückgeben, sich negativ auf die Leistung beeinträchtigen. Weitere Informationen finden Sie unter [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Eine Warnung dieser Regel wird dringend abgeraten. Fast kein Szenario auftreten, in denen der Inhalt eines schreibgeschützten Felds nicht von Bedeutung sind. Wenn dies Ihr Szenario zutrifft, entfernen Sie die `readonly` Modifizierer anstelle der Meldung auszuschließen.

## <a name="example-1"></a>Beispiel 1

Dieses Beispiel veranschaulicht die Gefahren des Verstoßes gegen diese Regel. Im ersten Teil wird eine Beispielbibliothek, deren Typ, `MyClassWithReadOnlyArrayField`, zwei Felder (`grades` und `privateGrades`), die nicht sicher sind. Das Feld `grades` ist öffentlich und daher anfällig für jeden Aufrufer. Das Feld `privateGrades` ist privat, aber nach wie vor anfällig ist, da es sich bei Rückgabe an den Aufrufer von der `GetPrivateGrades` Methode. Die `securePrivateGrades` -Feld verfügbar gemacht wird, auf sichere Weise durch die `GetSecurePrivateGrades` Methode. Es ist für gute designmethoden führen als privat deklariert. Der zweite Teil enthält Code, der in gespeicherten Werte ändert die `grades` und `privateGrades` Member.

Im folgenden Beispiel wird die Beispiel-Klassenbibliothek angezeigt.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Beispiel 2

Der folgende Code verwendet die Beispiel-Klassenbibliothek, um schreibgeschütztes Array von Sicherheitsproblemen zu veranschaulichen.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

Die Ausgabe dieses Beispielcodes ist:

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="related-rules"></a>Verwandte Regeln

- [CA2104 : Schreibgeschützte änderbare Referenztypen nicht deklarieren](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
