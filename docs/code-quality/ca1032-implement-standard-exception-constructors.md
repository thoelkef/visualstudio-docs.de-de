---
title: 'CA1032: Standardausnahmekonstruktoren implementieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454751"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standardausnahmekonstruktoren implementieren

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> aber nicht alle erforderlichen Konstruktoren deklariert.

## <a name="rule-description"></a>Regelbeschreibung

Ausnahmetypen müssen die folgenden drei Konstruktoren implementieren:

- Öffentliche NewException()

- Öffentliche NewException(string)

- Öffentliche NewException (String, Ausnahme)

Wenn Sie ältere für FxCop statische Codeanalyse als ausführen darüber hinaus dagegen spricht, [Roslyn-basierten FxCop-Analyzern](../code-quality/roslyn-analyzers-overview.md), Abwesenheit eine vierte Konstruktor generiert außerdem eine Verletzung:

- geschützt oder privat NewException (SerializationInfo, StreamingContext)

Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. Z. B. des Konstruktors, der die Signatur hat `NewException(string, Exception)` wird verwendet, um Ausnahmen zu erstellen, die von anderen Ausnahmen verursacht werden. Ohne diesen Konstruktor nicht erstellen, und lösen eine Instanz der benutzerdefinierten Ausnahme, die eine interne (geschachtelte) Ausnahme enthält, welche verwalteter Code in einer solchen Situation ausführen soll.

Die ersten drei Standardausnahmekonstruktoren sind gemäß der Konvention öffentlich. Der vierte Konstruktor ist in nicht versiegelten Klassen geschützt und privat in versiegelten Klassen. Weitere Informationen finden Sie unter [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die fehlenden Konstruktoren auf die Ausnahme, und stellen Sie sicher, dass sie die richtige Zugriffsebene aufweisen.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Verletzung verursacht wird, eine andere Zugriffsebene für die öffentlichen Konstruktoren mit. Darüber hinaus ist es angemessen, Unterdrückung der Warnung für die `NewException(SerializationInfo, StreamingContext)` Konstruktor, wenn Sie eine Portable Klassenbibliothek (PCL) erstellen.

## <a name="example"></a>Beispiel

Das folgende Beispiel enthält einen Ausnahmetyp, der mit dieser Regel verletzt und einen Ausnahmetyp, der ordnungsgemäß implementiert ist.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Siehe auch

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)