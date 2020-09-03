---
title: 'CA1052: statische Halter Typen sollten versiegelt sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539749"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statische Haltertypen sollten versiegelt sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält nur statische Member und ist nicht mit dem [versiegelten](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([notvererable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9))-Modifizierer deklariert.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel geht davon aus, dass ein Typ, der nur statische Member enthält, nicht für die Vererbung konzipiert ist, da der Typ keine Funktionen bereitstellt, die in einem abgeleiteten Typ überschrieben werden können. Ein Typ, der nicht vererbt werden soll, sollte mit dem- `sealed` Modifizierer gekennzeichnet werden, um die Verwendung als Basistyp zu verhindern.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie den Typ als `sealed` . Wenn Sie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] auf 2,0 oder früher abzielen, empfiehlt es sich, den Typ als zu markieren `static` . Auf diese Weise müssen Sie keinen privaten Konstruktor deklarieren, um zu verhindern, dass die Klasse erstellt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, wenn der Typ für die Vererbung entworfen wurde. Das Fehlen des `sealed` Modifizierers deutet darauf hin, dass der Typ als Basistyp nützlich ist.

## <a name="example-of-a-violation"></a>Beispiel für eine Verletzung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

### <a name="code"></a>Code
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Behebung mit dem statischen Modifizierer

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Beispiel wird gezeigt, wie ein Verstoß gegen diese Regel behoben werden kann, indem der-Typ mit dem- `static` Modifizierer gekennzeichnet wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
