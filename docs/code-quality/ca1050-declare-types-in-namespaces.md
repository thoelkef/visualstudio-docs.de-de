---
title: "CA1050: Typen in Namespaces deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1050: Typen in Namespaces deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ ist außerhalb des Gültigkeitsbereichs eines benannten Namespaces definiert.  
  
## Regelbeschreibung  
 Typen werden innerhalb von Namespaces deklariert, um Namenskonflikte zu verhindern und um verwandte Typen in einer Objekthierarchie zu organisieren.  Typen außerhalb eines benannten Namespaces befinden sich in einen globalen Namespace, auf den im Code nicht verwiesen werden kann.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie den Typ in einen Namespace ein.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Zwar ist es niemals notwendig, eine Warnung dieser Regel zu unterdrücken, doch ist dies gefahrlos möglich, wenn die Assembly nie zusammen mit anderen Assemblys verwendet wird.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Bibliothek mit einem Typ, der in unzulässiger Weise außerhalb eines Namespaces deklariert ist, und einen gleichnamigen Typ, der in einem Namespace deklariert ist.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Beispiel  
 Die folgende Anwendung verwendet die zuvor definierte Bibliothek.  Sie sehen, dass der außerhalb eines Namespaces deklarierte Typ erstellt wird, wenn der Name `Test` nicht durch einen Namespace qualifiziert wird.  Beachten Sie zudem, dass für den Zugriff auf den `Test`\-Typ in `Goodspace` der Namespacename benötigt wird.  
  
 [!code-cs[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]