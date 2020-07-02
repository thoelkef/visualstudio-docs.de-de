---
title: 'CA1023: Indexer sollten nicht mehrdimensional sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546647"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indexer sollten nicht mehrdimensional sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer, der mehr als einen Index verwendet.

## <a name="rule-description"></a>Beschreibung der Regel
 Indexer, d. h. indizierte Eigenschaften, sollten einen einzelnen Index verwenden. Mehrdimensionale Indexer können die Verwendbarkeit der Bibliothek erheblich verringern. Wenn der Entwurf mehrere Indizes erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn dies nicht der gibt, verwenden Sie eine-Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass er eine Ganzzahl oder einen Zeichen folgen Index verwendet, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, nachdem sorgfältig geprüft wurde, dass es sich nicht um einen Standardindexer handelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen-Typ `DayOfWeek03` mit einem mehrdimensionalen Indexer, der gegen die Regel verstößt. Der Indexer kann als Konvertierungstyp angesehen werden und wird daher besser als-Methode verfügbar gemacht. Der Typ wird in umgestaltet `RedesignedDayOfWeek03` , um die Regel zu erfüllen.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden.](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Nach Möglichkeit Eigenschaften verwenden.](../code-quality/ca1024-use-properties-where-appropriate.md)
