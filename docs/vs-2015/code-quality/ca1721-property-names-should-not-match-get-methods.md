---
title: 'CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d120a7656fc9270543ceeb57063124764c4bca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431189"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und entspricht andernfalls den Namen einer öffentlichen oder geschützten Eigenschaft. Ein Typ, der eine Methode, mit dem Namen enthält "GetColor" und eine Eigenschaft mit dem Namen "Farbe" z. B. verletzt diese Regel.

## <a name="rule-description"></a>Regelbeschreibung
 Get-Methoden und Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek erfahren, und zudem wird das Kundenvertrauen, dass die Bibliothek von einer Person entwickelt wurde, die Erfahrung in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen ein, sodass sie nicht den Namen einer Methode übereinstimmt, der mit "Get" vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

> [!NOTE]
> Diese Warnung kann ausgeschlossen werden, wenn die Get-Methode verursacht wird, indem Sie IExtenderProvider-Schnittstelle implementieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält eine Methode und eine Eigenschaft, die gegen diese Regel verstoßen.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md)
