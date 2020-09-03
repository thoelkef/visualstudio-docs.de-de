---
title: 'CA1813: nicht versiegelte Attribute vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543948"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Nicht versiegelte Attribute vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ erbt von <xref:System.Attribute?displayProperty=fullName> , ist nicht abstrakt und ist nicht versiegelt ( `NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Beschreibung der Regel
 Die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek stellt Methoden zum Abrufen benutzerdefinierter Attribute bereit. Standardmäßig durchsuchen diese Methoden die Attribut Vererbungs Hierarchie. beispielsweise <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> sucht nach dem angegebenen Attributtyp oder nach einem beliebigen Attributtyp, der den angegebenen Attributtyp erweitert. Durch das Versiegeln des Attributs wird die Suche durch die Vererbungs Hierarchie beseitigt und die Leistung verbessert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, versiegeln Sie den Attributtyp, oder machen Sie ihn abstrakt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Dies sollten Sie nur tun, wenn Sie eine Attribut Hierarchie definieren und das Attribut nicht versiegeln oder abstrakt machen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein benutzerdefiniertes Attribut, das diese Regel erfüllt.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1019: Accessoren für Attributargumente definieren.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Attribute mit AttributeUsageAttribute markieren.](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Weitere Informationen
 [Attribute](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
