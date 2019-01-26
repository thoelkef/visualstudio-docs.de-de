---
title: 'CA1032: Standardausnahmekonstruktoren implementieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 947b22929c58ce962861c65946941513d7845152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957781"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standardausnahmekonstruktoren implementieren.

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> , aber nicht alle erforderlichen Konstruktoren deklariert.

## <a name="rule-description"></a>Regelbeschreibung

Typen müssen die folgenden drei Konstruktoren implementieren:

- public NewException()

- Öffentliche NewException(string)

- Öffentliche NewException (String, Ausnahme)

Wenn Sie ältere für FxCop statische Codeanalyse als ausführen, außerdem im Gegensatz zu [FxCop auf Roslyn basierende Analysetools](../code-quality/roslyn-analyzers-overview.md), das Fehlen einer vierten Konstruktor generiert außerdem eine Verletzung:

- geschützt oder privat NewException (SerializationInfo-Objekt, StreamingContext)

Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. Z. B. der Konstruktor mit der Signatur `NewException(string, Exception)` wird verwendet, um Ausnahmen zu erstellen, die von anderen Ausnahmen verursacht werden. Ohne diesen Konstruktor kann nicht erstellt und lösen eine Instanz der benutzerdefinierten Ausnahme, die von einer inneren (geschachtelten)-Ausnahme enthält, welche verwalteter Code in einem solchen Fall tun.

Die ersten drei Standardausnahmekonstruktoren sind standardmäßig öffentlich. Der vierte Konstruktor ist in nicht versiegelte Klassen geschützt und im versiegelte Klassen privat. Weitere Informationen finden Sie unter [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die fehlenden Konstruktoren, auf die Ausnahme, und stellen Sie sicher, dass sie die richtige Zugriffsebene verfügen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn die Verletzung verursacht wird, eine andere Zugriffsebene für die öffentlichen Konstruktoren mit. Darüber hinaus ist es in Ordnung ist, unterdrückt die Warnung für die `NewException(SerializationInfo, StreamingContext)` Konstruktor, wenn Sie eine Portable Klassenbibliothek (PCL) erstellen.

## <a name="example"></a>Beispiel

Das folgende Beispiel enthält einen Ausnahmetyp, der gegen diese Regel verstößt und einem Ausnahmetyp, der ordnungsgemäß implementiert ist.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Siehe auch

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)