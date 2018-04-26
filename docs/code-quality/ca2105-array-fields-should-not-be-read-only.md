---
title: 'CA2105: Arrayfelder dürfen nicht schreibgeschützt sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91a97983a8760d7f5df04fe6e5b0a56a782a11ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Arrayfelder dürfen nicht schreibgeschützt sein
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Feld, das ein Array enthält, ist schreibgeschützt deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Beim Anwenden der `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Modifizierer, um ein Feld, das ein Array, das Feld enthält kann nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. Code, der entscheidet oder führt Vorgänge, die die Elemente eines Arrays ohne Schreibzugriff basieren, die öffentlich zugegriffen werden kann, kann ein ausnutzbares Sicherheitsrisiko enthalten.

 Beachten Sie, dass das Vorhandensein eines öffentlichen Felds auch das Entwurfsregel verletzt [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Sicherheitsrisiko zu beheben, das von dieser Regel identifiziert wird, verlassen Sie sich nicht auf den Inhalt eines Arrays ohne Schreibzugriff, die öffentlich zugegriffen werden kann. Es wird dringend empfohlen, dass Sie eine der folgenden Verfahren verwenden:

-   Ersetzen Sie das Array durch eine stark typisierte Auflistung, die nicht geändert werden kann. Weitere Informationen finden Sie unter <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Ersetzen Sie das öffentliche Feld mit einer Methode, die einen Klon eines privaten Arrays zurückgibt. Da der Code nicht auf dem Klon abhängig wird, besteht keine Gefahr, wenn die Elemente geändert werden.

 Wenn Sie den zweiten Ansatz gewählt haben, ersetzen Sie das Feld nicht mit einer Eigenschaft; Eigenschaften, die Arrays zurückgeben, negativ auf die Leistung beeinträchtigen. Weitere Informationen finden Sie unter [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Eine Warnung dieser Regel wird dringend abgeraten. Fast keine Szenarien auftreten, in denen der Inhalt eines schreibgeschützten Felds nicht von Bedeutung sind. Wenn dies auf Ihr Szenario zutrifft, entfernen Sie die `readonly` Modifizierer anstelle der Meldung auszuschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt die Gefahren Verstoß gegen diese Regel. Der erste Teil zeigt eine Beispielbibliothek, die ein Typ hat `MyClassWithReadOnlyArrayField`, enthält zwei Felder (`grades` und `privateGrades`), die nicht sicher sind. Das Feld `grades` ist öffentlich und kann daher für jeden Aufrufer angegriffen. Das Feld `privateGrades` privat, jedoch ist immer noch anfällig sind, da er auf vom Aufrufer zurückgegeben wird, die `GetPrivateGrades` Methode. Die `securePrivateGrades` Feld verfügbar gemacht wird, auf sichere Weise durch die `GetSecurePrivateGrades` Methode. Er wird um guten Entwurf Vorgehensweisen als privat deklariert. Der zweite Teil enthält Code, der in gespeicherten Werte ändert die `grades` und `privateGrades` Elemente.

 Im folgenden Beispiel wird die Klassenbibliothek wird angezeigt.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Beispiel
 Der folgende Code verwendet die Beispiel-Klassenbibliothek schreibgeschütztes Array von Sicherheitsproblemen zu veranschaulichen.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 Die Ausgabe dieses Beispiels ist:

 **Vor Manipulation: Qualitäten: 90, 90, 90 Private Grade: 90, 90, 90 sichere Grade, 90, 90, 90**
**nach Manipulation: Qualitäten: 90, 555, 90 Private Grade: 90, 555, 90 sichere Grade, 90, 90, 90**
## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>