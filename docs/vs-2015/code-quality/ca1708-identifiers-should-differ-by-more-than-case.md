---
title: 'CA1708: Bezeichner sollten sich um mehr als den Fall unterscheiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22a33c852b941b4c7e7398416aa1e74e69ff1786
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544039"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die Namen von zwei Typen, Membern, Parametern oder voll qualifizierten Namespaces sind identisch, wenn Sie in Kleinbuchstaben konvertiert werden.

## <a name="rule-description"></a>Beschreibung der Regel
 Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen. Beispielsweise [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ist eine häufig verwendete Sprache ohne Beachtung der Groß-/Kleinschreibung.

 Diese Regel wird nur für öffentlich sichtbare Elemente ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen eindeutigen Namen aus, wenn er mit anderen bezeichnerwerten in der Groß-und Kleinschreibung verglichen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Die Bibliothek ist möglicherweise nicht in allen verfügbaren Sprachen in der verwendbar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung
 Das folgende Beispiel veranschaulicht einen Verstoß gegen diese Regel.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
