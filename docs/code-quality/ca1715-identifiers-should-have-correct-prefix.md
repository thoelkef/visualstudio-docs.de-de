---
title: 'CA1715: Bezeichner sollten ein korrektes Präfix aufweisen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c7abdaa2356bdf622f0892e9b027047fc021096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912924"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Bezeichner sollten ein korrektes Präfix aufweisen

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Wichtige – Wenn auf Schnittstellen ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für den generischen Parameter des Typs ausgelöst.|

## <a name="cause"></a>Ursache
 Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem Großbuchstaben "I".

 - oder - 

 Der Name der einen generischen Parameter für einen extern sichtbaren Typ oder Methode beginnt nicht mit einem Großbuchstaben ' t '.

## <a name="rule-description"></a>Regelbeschreibung
 Starten die Namen der bestimmte Programmierelemente gemäß der Konvention mit einem bestimmten Präfix.

 Schnittstellennamen sollte mit einem großen gestartet werden die 'I' einen anderen Großbuchstabe folgen. Diese Regel wird berichtet, Verstöße für Schnittstellennamen, z. B. "MyInterface" und "IsolatedInterface".

 Namen generischer Typparameter sollte mit einem Großbuchstaben beginnen ' t ' und kann optional von einem anderen Großbuchstaben gefolgt werden. Diese Regel wird berichtet, Verstöße für den Namen des generischen Typs Parameter wie z. B. 'V' und 'Typ'.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Benennen Sie den Bezeichner, damit es ordnungsgemäß vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 **Das folgende Beispiel zeigt eine falsch benannte Schnittstelle.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Beispiel
 **Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem Sie die Schnittstelle 'I' voranstellen.**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Beispiel
 **Das folgende Beispiel zeigt einen falsch benannter generischer Typparameter.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>Beispiel
 **Im folgenden Beispiel wird der vorherige Verstoß durch voranstellen des generischen Typparameters t korrigiert ".**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)