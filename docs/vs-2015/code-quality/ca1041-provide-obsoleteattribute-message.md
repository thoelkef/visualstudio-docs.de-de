---
title: 'CA1041: ObsoleteAttribute-Meldung bereitstellen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668326"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute-Meldung bereitstellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ oder Member wird mithilfe eines <xref:System.ObsoleteAttribute?displayProperty=fullName> Attributs gekennzeichnet, dessen <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>-Eigenschaft nicht angegeben ist.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.ObsoleteAttribute> wird verwendet, um veraltete Bibliothekstypen und Member zu markieren. Bibliotheks Consumer sollten die Verwendung eines beliebigen Typs oder Members vermeiden, der als veraltet markiert ist. Dies liegt daran, dass Sie möglicherweise nicht unterstützt wird und schließlich aus späteren Versionen der Bibliothek entfernt wird. Wenn ein Typ oder Member, der mit <xref:System.ObsoleteAttribute> gekennzeichnet ist, kompiliert wird, wird die <xref:System.ObsoleteAttribute.Message%2A>-Eigenschaft des Attributs angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. Diese Informationen umfassen im Allgemeinen, wie lange der veraltete Typ oder Member von den Bibliotheks-Designern unterstützt wird, und die bevorzugte Ersetzung für die Verwendung von.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem <xref:System.ObsoleteAttribute>-Konstruktor den `message`-Parameter hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung aus dieser Regel, da die <xref:System.ObsoleteAttribute.Message%2A>-Eigenschaft wichtige Informationen über den veralteten Typ oder Member bereitstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein veraltetes Element, das über eine ordnungsgemäß deklarierte <xref:System.ObsoleteAttribute> verfügt.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
