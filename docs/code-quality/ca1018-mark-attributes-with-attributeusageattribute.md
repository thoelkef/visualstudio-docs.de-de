---
title: 'CA1018: Attribute mit AttributeUsageAttribute markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b94cb7c11c803e713609036db12c47e2027cb61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Attribute mit AttributeUsageAttribute markieren
|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Die <xref:System.AttributeUsageAttribute?displayProperty=fullName> -Attribut nicht auf das benutzerdefinierte Attribut vorhanden ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mit <xref:System.AttributeUsageAttribute> , um anzugeben, wo im Quellcode das benutzerdefinierte Attribut angewendet werden können. Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code. Sie können z. B. ein Attribut definieren, die identifiziert die Person, die verantwortlich für die Wartung und Verbesserung jedes Typs in einer Bibliothek und Verantwortung wird immer auf Typebene zugewiesen. In diesem Fall Compiler sollte das Attribut auf Klassen, Enumerationen und Schnittstellen aktivieren, jedoch sollten nicht auf Methoden, Ereignisse oder Eigenschaften aktivieren. Unternehmensrichtlinien und Prozeduren würde bestimmen, ob das Attribut Assemblys aktiviert werden soll.  
  
 Die <xref:System.AttributeTargets?displayProperty=fullName> -Enumeration definiert die Ziele, die Sie für ein benutzerdefiniertes Attribut angeben können. Wenn Sie weglassen <xref:System.AttributeUsageAttribute>, das benutzerdefinierte Attribut wird für alle Ziele gültig sein, gemäß der `All` Wert <xref:System.AttributeTargets> Enumeration.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie Ziele für das Attribut mit <xref:System.AttributeUsageAttribute>. Weitere Informationen finden Sie im folgenden Beispiel.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie sollten einen Verstoß gegen diese Regel statt mit Ausnahme der Nachrichteninhalts reparieren. Auch wenn das Attribut erbt <xref:System.AttributeUsageAttribute>, das Attribut muss vorhanden sein, damit Wartung des Programmcodes vereinfachen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel definiert zwei Attribute. `BadCodeMaintainerAttribute`falsch lässt die <xref:System.AttributeUsageAttribute> -Anweisung und `GoodCodeMaintainerAttribute` ordnungsgemäß implementiert das Attribut, das weiter oben in diesem Abschnitt beschrieben wird. Beachten Sie, dass die Eigenschaft `DeveloperName` ist erforderlich, durch die Entwurfsregel [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) und wird aus Gründen der Vollständigkeit.  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1019: Zugriffsmethoden für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute](/dotnet/standard/design-guidelines/attributes)