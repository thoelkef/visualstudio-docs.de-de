---
title: 'CA1052: Statische Haltertypen sollten versiegelt | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: deb02958ac89c350c4dc616b68693ee41b3019f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Statische Haltertypen sollten versiegelt sein
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ enthält nur statische Member und ist nicht deklariert, mit der [versiegelten](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) Modifizierer.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel setzt voraus, dass ein Typ, der nur statische Member enthält nicht geerbt werden, konzipiert ist, da der Typ keine Funktionalität bereit, die in einem abgeleiteten Typ überschrieben werden können. Ein Typ, der nicht geerbt werden soll gekennzeichnet werden, mit der `sealed` Modifizierer, um seine Verwendung als Basistyp zu verhindern.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie den Typ als `sealed`. Wenn die anvisierten [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 oder höher, wird ein besserer Ansatz ist, markieren Sie den Typ als `static`. Auf diese Weise vermeiden Sie deklarieren Sie einen privaten Konstruktor, um zu verhindern, dass die Klasse erstellt wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn der Typ geerbt werden soll. Das Fehlen der `sealed` Modifizierers impliziert, dass der Typ als Basistyp nützlich ist.  
  
## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Beheben von mit der Static-Modifizierer  
  
### <a name="description"></a>Beschreibung  
 Im folgende Beispiel wird gezeigt, wie einen Verstoß gegen diese Regel zu beheben, indem Sie den Typ mit dem `static` Modifizierer.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
