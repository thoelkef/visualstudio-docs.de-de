---
title: 'CA2222: Sichtbarkeit für geerbte Elemente nicht verringern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04109e821d3a739b96ad63e1a441089a5d479cd8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540776"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Sichtbarkeit für geerbte Member nicht verringern.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine private Methode in einem nicht versiegelten Typ hat eine Signatur, die mit einer öffentlichen Methode identisch ist, die in einem Basistyp deklariert ist. Die private Methode ist nicht Final.

## <a name="rule-description"></a>Beschreibung der Regel
 Sie sollten den Zugriffsmodifizierer für geerbte Member nicht ändern. Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert. Wenn der Member privat gemacht wird und der Typ nicht versiegelt ist, kann der erbende Typ die letzte öffentliche Implementierung der Methode in der Vererbungs Hierarchie aufzurufen. Wenn Sie den Zugriffsmodifizierer ändern müssen, muss entweder die Methode als Final markiert werden, oder der Typ muss versiegelt sein, um zu verhindern, dass die Methode überschrieben wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff auf "nicht privat". Wenn Ihre Programmiersprache Sie unterstützt, können Sie alternativ die Methode als endgültig festlegen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
