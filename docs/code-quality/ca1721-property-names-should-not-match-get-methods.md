---
title: 'CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29db0561f15a16bf9b449f03f209feedf80dbd88
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen
|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name des ein öffentlicher oder geschützter Member beginnt mit "Get" und entspricht, andernfalls den Namen einer öffentlichen oder geschützten-Eigenschaft. Ein Typ, der eine Methode, die Namen enthält "GetColor" und eine Eigenschaft mit dem Namen 'Color' beispielsweise verletzt diese Regel.

## <a name="rule-description"></a>Regelbeschreibung
 Get-Methoden und Eigenschaften sollten über Namen verfügen, die ihre Funktion klar zu unterscheiden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek Informationen zu erhalten, zudem wird, dass die Bibliothek von einem Benutzer, Kenntnisse in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen ein, sodass sie nicht den Namen einer Methode übereinstimmt, der mit "Get" vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

> [!NOTE]
>  Diese Warnung kann ausgeschlossen werden, die Get-Methode durch Implementieren der Schnittstelle IExtenderProvider-verursacht.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält eine Methode und Eigenschaft, die diese Regel verletzen.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)