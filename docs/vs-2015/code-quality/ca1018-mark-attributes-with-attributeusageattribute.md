---
title: 'CA1018: Attribute mit AttributeUsageAttribute markieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f278a64b1626e94ce55eef6fb8e403d4a5db9cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246934"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Attribute mit AttributeUsageAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die <xref:System.AttributeUsageAttribute?displayProperty=fullName> Attribut ist nicht vorhanden ist, auf das benutzerdefinierte Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von <xref:System.AttributeUsageAttribute> , um anzugeben, im Quellcode das benutzerdefinierte Attribut angewendet werden kann. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. Sie können z. B. ein Attribut definieren, die die Person, die angibt, wer ist verantwortlich für die Wartung und Verbesserung jedes Typs in einer Bibliothek und Verantwortung wird immer auf Typebene zugewiesen. In diesem Fall Compiler sollten das Attribut auf Klassen, Enumerationen und Schnittstellen aktivieren, jedoch sollten sie nicht auf Methoden, Ereignisse oder Eigenschaften aktivieren. Organisatorischen Richtlinien und Verfahren würden Sie bestimmen, ob das Attribut für Assemblys aktiviert werden soll.

 Die <xref:System.AttributeTargets?displayProperty=fullName> -Enumeration definiert die Ziele, die Sie für ein benutzerdefiniertes Attribut angeben können. Wenn Sie weglassen <xref:System.AttributeUsageAttribute>, das benutzerdefinierte Attribut wird für alle Ziele werden, gemäß der `All` Wert <xref:System.AttributeTargets> Enumeration.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie Ziele für das Attribut mit <xref:System.AttributeUsageAttribute>. Weitere Informationen finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten einen Verstoß gegen diese Regel mit Ausnahme der Nachricht beheben. Auch wenn das Attribut erbt <xref:System.AttributeUsageAttribute>, das Attribut muss vorhanden sein, damit Wartung des Programmcodes vereinfachen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert zwei Attribute. `BadCodeMaintainerAttribute` falsch lässt die <xref:System.AttributeUsageAttribute> -Anweisung und `GoodCodeMaintainerAttribute` korrekt implementiert das Attribut, das weiter oben in diesem Abschnitt beschrieben wird. Beachten Sie, dass die Eigenschaft `DeveloperName` ist erforderlich, die von der Regel entwerfen [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) und wird aus Gründen der Vollständigkeit.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1019: Zugriffsmethoden für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Siehe auch
 [Attribute](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



