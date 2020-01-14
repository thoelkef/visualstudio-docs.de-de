---
title: 'CA1801: nicht verwendete Parameter überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918169"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Nicht verwendete Parameter überprüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1801: Überprüfen von nicht verwendeten Parametern](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der Member außerhalb der Assembly nicht sichtbar ist, unabhängig von der Änderung, die Sie vornehmen.<br /><br /> Nicht unterbrechend: Wenn Sie den Member so ändern, dass er den-Parameter innerhalb seines Texts verwendet.<br /><br /> Unterbrechen: Wenn Sie den Parameter entfernen und dieser außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. Diese Regel untersucht nicht die folgenden Methoden:

- Methoden, auf die ein Delegat verweist.

- Methoden, die als Ereignishandler verwendet werden.

- Methoden, die mit dem `abstract`-Modifizierer (`MustOverride` in Visual Basic) deklariert wurden.

- Methoden, die mit dem `virtual`-Modifizierer (`Overridable` in Visual Basic) deklariert wurden.

- Methoden, die mit dem `override`-Modifizierer (`Overrides` in Visual Basic) deklariert wurden.

- Methoden, die mit dem `extern`-Modifizierer (`Declare` Anweisung in Visual Basic) deklariert wurden.

## <a name="rule-description"></a>Regelbeschreibung
 Überprüfen Sie Parameter in nicht virtuellen Methoden, die nicht im Methoden Text verwendet werden, um sicherzustellen, dass keine Richtigkeit bei einem Fehler auftritt. Nicht verwendete Parameter verursachen Wartungs-und Leistungskosten.

 Manchmal kann ein Verstoß gegen diese Regel auf einen Implementierungs Fehler in der-Methode hinweisen. Beispielsweise sollte der-Parameter im Methoden Text verwendet werden. Unterdrückt Warnungen dieser Regel, wenn der Parameter aufgrund der Abwärtskompatibilität vorhanden sein muss.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter (a Breaking Change), oder verwenden Sie den-Parameter im Methoden Text (ein nicht-Breaking Change).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel für den zuvor gelieferten Code zu unterdrücken, dessen Behebung eine Breaking Change wäre.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden. Eine Methode verstößt gegen die Regel, und die andere Methode erfüllt die Regel.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
