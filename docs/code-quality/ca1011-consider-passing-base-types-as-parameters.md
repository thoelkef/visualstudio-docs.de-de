---
title: 'CA1011: Basistypen als Parameter übergeben'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac73d2be980791d41b172ba0669387fd68a331fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Basistypen als Parameter übergeben
|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methodendeklaration enthält einen formalen Parameter, der ein abgeleiteter Typ ist, und die Methode ruft nur Member des Basistyps des Parameters.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden. Wenn das Argument innerhalb des Methodentexts verwendet wird, hängt die jeweilige Methode, die ausgeführt wird der Typ des Arguments ab. Wenn die zusätzliche Funktionalität, die vom abgeleiteten Typ bereitgestellt wird, nicht erforderlich ist, ermöglicht die Verwendung des Basistyps eine allgemeinere Nutzung der Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ des Parameters mit seinem Basistyp.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können zum Unterdrücken einer Warnung dieser Regel ruhig

-   Wenn die Methode die spezifische Funktionalität benötigt, die vom abgeleiteten Typ bereitgestellt wird

     \- oder –

-   um zu erzwingen, dass nur der abgeleitete Typ oder einen stärker abgeleiteten Typ. an die Methode übergeben wird.

 In diesen Fällen wird der Code sein eine robustere aufgrund der starken typüberprüfung, die durch den Compiler und die Common Language Runtime bereitgestellt wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode `ManipulateFileStream`, die verwendet werden kann, nur mit einem <xref:System.IO.FileStream> -Objekt, das mit dieser Regel verletzt. Einer zweiten Methode `ManipulateAnyStream`, der durch Ersetzen der Regel entspricht der <xref:System.IO.FileStream> Parameter, indem eine <xref:System.IO.Stream>.

 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)