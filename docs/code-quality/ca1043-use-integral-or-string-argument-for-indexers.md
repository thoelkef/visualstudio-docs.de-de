---
title: 'CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3d47b39208fce297fd058d6976b9fa7d7593cb9a
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867150"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ enthält, einen Indexer, der einen Indextyp verwendet <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, oder <xref:System.String?displayProperty=fullName>.

Diese Regel nur sucht standardmäßig an öffentliche und geschützte Typen. Dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Indexer, d. h. indizierte Eigenschaften sollten ganze Zahl oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. r. zum Indizieren von Datenstrukturen verwendet, und erweitern den Einsatzbereich der Bibliothek. Verwenden der <xref:System.Object> Typ Fälle, in dem der spezifische Typ für ganze Zahl oder Zeichenfolge kann nicht zur Entwurfszeit angegeben werden kann, eingeschränkt werden soll. Wenn der Entwurf andere Typen für den Index erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn sie einen logischen Datenspeicher keine darstellt, verwenden Sie eine Methode an.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Index in eine ganze Zahl oder Zeichenfolge-Typ, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel erst nach den Bedarf für den Indexer nicht dem Standard entsprechende sorgfältig geprüft.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1043.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Indexer, der verwendet eine <xref:System.Int32> Index.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1023: Indexer sollten nicht mehrdimensional sein.](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024: Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md)