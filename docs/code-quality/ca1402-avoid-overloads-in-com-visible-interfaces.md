---
title: "CA1402: &#220;berladungen in f&#252;r COM sichtbaren Schnittstellen vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: &#220;berladungen in f&#252;r COM sichtbaren Schnittstellen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine sichtbare Component Object Model \(COM\)\-Schnittstelle deklariert überladene Methoden.  
  
## Regelbeschreibung  
 Wenn für COM\-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen.  Nachfolgende Überladungen werden eindeutig umbenannt, indem dem Namen ein Unterstrich \('\_'\) und eine ganze Zahl angefügt werden, die der Reihenfolge der Deklaration der Überladung entspricht.  Betrachten Sie z. B. die folgenden Methoden:  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Diese Methoden werden COM\-Clients wie folgt verfügbar gemacht.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6\-COM\-Clients können keine Schnittstellenmethoden mit einem Unterstrich im Namen implementieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die überladenen Methoden um, sodass die Namen eindeutig sind.  Sie können die Schnittstelle auch für COM sichtbar machen, indem Sie die Zugriffsart in `internal` ändern \(`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) oder das auf `false` festgelegte <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>\-Attribut übernehmen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Schnittstelle, die gegen die Regel verstößt, und eine Schnittstelle, die der Regel entspricht.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Verwandte Regeln  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)