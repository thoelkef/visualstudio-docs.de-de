---
title: "CA1019: Accessors für Attributargumente definieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1c67e5963cdac0c9398ee2e4d54a4cd3347fee66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Accessors für Attributargumente definieren
|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 In seinem Konstruktor definiert ein Attribut Argumente, die nicht über die entsprechende Eigenschaften verfügen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird. Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden. Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann. Diese Regel überprüft, dass für jeden Konstruktorparameter, Sie die entsprechende Eigenschaft definiert haben.  
  
 Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden. Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese-Schreib-Eigenschaft verfügen.  
  
 Der gleiche name aber abweichender Groß-/Kleinschreibung, für obligatorische und optionale Argumente, die entsprechenden Eigenschaften und Konstruktorparameter verwendet werden soll. Verwenden Sie Eigenschaften wie in Pascal-Schreibweise und Parameter Kamel-Schreibweise verwendet.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine schreibgeschützte Eigenschaft, für jeden Parameter des Konstruktors, die Sie nicht besitzt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass den Wert des Arguments obligatorische abrufbar sein möchten.  
  
## <a name="custom-attributes-example"></a>Beispiel für benutzerdefinierte Attribute  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt zwei Attribute, die einen obligatorischen Parameter (mit Feldern fester Breite) zu definieren. Die erste Implementierung des Attributs ist falsch definiert. Die zweite Implementierung ist richtig.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## <a name="positional-and-named-arguments"></a>Mit Feldern fester Breite und benannte Argumente  
  
### <a name="description"></a>Beschreibung  
 Mit Feldern fester Breite und benannte Argumente stellen für Consumer Ihrer Bibliothek löschen, werden die Argumente für das Attribut und die Argumente sind optional.  
  
 Das folgende Beispiel zeigt eine Implementierung eines Attributs, das mit Feldern fester Breite und benannte Argumente verfügt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### <a name="comments"></a>Kommentare  
 Im folgende Beispiel wird gezeigt, wie das benutzerdefinierte Attribut auf zwei Eigenschaften angewendet werden.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute](/dotnet/standard/design-guidelines/attributes)