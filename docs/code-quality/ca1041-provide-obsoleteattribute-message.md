---
title: 'CA1041: ObsoleteAttribute-Meldung bereitstellen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc851ef4b4ef1cdca9bdb1f9692d3bbc7f0a795c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute-Meldung bereitstellen
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ oder Member mit RuntimeCompatibility eine <xref:System.ObsoleteAttribute?displayProperty=fullName> -Attribut, das keinen seine <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> angegebene Eigenschaft.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.ObsoleteAttribute> wird verwendet, um veraltete Bibliothekstypen und Member zu markieren. Bibliotheksconsumer sollten die Verwendung von Typen oder Member, die als veraltet markiert ist. Dies ist, weil sie möglicherweise nicht unterstützt mehr und ggf. von späteren Versionen der Bibliothek entfernt werden wird. Wenn ein Typ oder Member mit markiert <xref:System.ObsoleteAttribute> kompiliert wird, die <xref:System.ObsoleteAttribute.Message%2A> Eigenschaft des Attributs wird angezeigt. Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member. Diese Informationen umfassen im Allgemeinen, wie langen den veralteten Typ oder Member wird durch die Bibliothek-Designer und der bevorzugte Ersatz verwenden unterstützt werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen die `message` Parameter an die <xref:System.ObsoleteAttribute> Konstruktor.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel da die <xref:System.ObsoleteAttribute.Message%2A> Eigenschaft enthält wichtigen Informationen zum veralteten Typ oder Member.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen veralteten Member, die über einen ordnungsgemäß deklarierten verfügt <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>