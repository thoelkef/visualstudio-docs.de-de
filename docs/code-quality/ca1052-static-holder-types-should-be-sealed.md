---
title: "CA1052: Statische Haltertypen sollten versiegelt sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1052: Statische Haltertypen sollten versiegelt sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ enthält nur statische Member und ist nicht mit dem [sealed](/dotnet/csharp/language-reference/keywords/sealed)\-Modifzierer \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\) deklariert.  
  
## Regelbeschreibung  
 Diese Regel setzt voraus, dass ein Typ, der nur statische Member enthält, nicht für die Vererbung konzipiert ist, da der Typ keine Funktionen angibt, die in einem abgeleiteten Typ überschrieben werden können.  Ein Typ, der nicht geerbt werden, muss mit dem `sealed`\-Modifizierer markiert werden, um seine Verwendung als Basistyp zu verhindern.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, kennzeichnen Sie den Typ als `sealed`.  Wenn Sie für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 oder früher entwickeln, ist die Markierung des Typs als `static` vorzuziehen.  Auf diese Weise müssen Sie keinen privaten Konstruktor deklarieren, um die Erstellung der Klasse zu verhindern.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur dann, wenn der Typ für die Vererbung konzipiert ist.  Die Abwesenheit des `sealed`\-Modifizierers impliziert, dass der Typ als Basistyp verwendet werden kann.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Korrektur mit dem static\-Modifizierer  
  
### **Beschreibung**  
 Das folgende Beispiel zeigt, wie eine Verletzung dieser Regeln korrigiert wird, indem der Typ mit dem `static`\-Modifizierer markiert wird.  
  
### Code  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Verwandte Regeln  
 [CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)