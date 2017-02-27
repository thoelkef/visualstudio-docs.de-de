---
title: "CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher Typ ist versiegelt und deklariert eine Methode, die sowohl `virtual` \(`Overridable` in Visual Basic\) als auch nicht final ist.  Diese Regel meldet keine Verstöße bei Delegattypen, die diesem Muster folgen müssen.  
  
## Regelbeschreibung  
 Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können.  Per Definition ist es nicht möglich, von einem versiegelten Typ zu erben. Dementsprechend ist eine virtuelle Methode auf einem versiegelten Typ bedeutungslos.  
  
 Bei Verwendung des Visual Basic .NET\-Compilers und des C\#\-Compilers ist ausgeschlossen, dass Typen gegen diese Regel verstoßen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie die Methode als nicht virtuelle Methode, oder machen Sie den Typ vererbbar.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Das Beibehalten des aktuellen Zustands des Typs kann Wartungsprobleme verursachen und bietet keine Vorteile.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]