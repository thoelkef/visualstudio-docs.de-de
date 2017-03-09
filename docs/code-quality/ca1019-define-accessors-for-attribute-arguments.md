---
title: "CA1019: Accessors f&#252;r Attributargumente definieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019: Accessors f&#252;r Attributargumente definieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Attribut definiert in seinem Konstruktor Argumente, die nicht über entsprechende Eigenschaften verfügen.  
  
## Regelbeschreibung  
 Attribute können obligatorische Argumente definieren, die angegeben werden müssen, wenn das Attribut auf ein Ziel angewendet wird.  Diese Argumente werden auch als positionelle Argumente bezeichnet, da sie bei Attributkonstruktoren als positionelle Parameter angegeben werden.  Für jedes obligatorische Argument muss das Attribut außerdem eine entsprechende schreibgeschützte Eigenschaft enthalten, damit der Wert des Arguments zur Ausführungszeit abgerufen werden kann.  Mit dieser Regel wird festgestellt, ob Sie für jeden Konstruktorparameter die entsprechende Eigenschaft definiert haben.  
  
 Attribute können auch optionale Argumente definieren, die auch als benannte Argumente bezeichnet werden.  Diese Argumente werden bei Attributkonstruktoren über ihren Namen angegeben und sollten über eine entsprechende Lese\-Schreib\-Eigenschaft verfügen.  
  
 Bei obligatorischen und optionalen Argumenten sollten für die entsprechenden Eigenschaften und Konstruktorparameter der gleiche Name, jedoch eine andere Schreibweise verwendet werden.  Bei Eigenschaften wird die Pascal\-Schreibweise, bei Parametern die Kamel\-Schreibweise verwendet.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine schreibgeschützte Eigenschaft für jeden Konstruktorparameter hinzu, der nicht über eine solche Eigenschaft verfügt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn der Wert des obligatorischen Arguments nicht abrufbar sein soll.  
  
## Beispiel für benutzerdefinierte Attribute  
  
### **Beschreibung**  
 Im folgenden Beispiel werden zwei Attribute veranschaulicht, die einen obligatorischen \(positionellen\) Parameter definieren.  Die erste Implementierung des Attributs ist fehlerhaft definiert.  Die zweite Implementierung ist einwandfrei.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## Positionsargumente und benannte Argumente  
  
### **Beschreibung**  
 Anhand von Positionsargumenten und benannten Argumenten wird Bibliotheksbenutzern verdeutlicht, welche Argumente für das Attribut zwingend und welche optional sind.  
  
 Im folgenden Beispiel wird eine Implementierung einen Attributs veranschaulicht, das sowohl über Positionsargumente als auch über benannte Argumente verfügt.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### Kommentare  
 Im folgenden Beispiel wird gezeigt, wie das benutzerdefinierte Attribut auf zwei Eigenschaften angewendet wird.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## Verwandte Regeln  
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Siehe auch  
 [Attribute](../Topic/Attributes1.md)