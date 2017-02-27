---
title: "CA1047: Gesch&#252;tzte Member in versiegelten Typen nicht deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1047: Gesch&#252;tzte Member in versiegelten Typen nicht deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher Typ ist `sealed` \(`NotInheritable` in Visual Basic\) und deklariert einen geschützten Member oder einen geschützten geschachtelten Typ.  Diese Regel meldet keine Verstöße bei <xref:System.Object.Finalize%2A>\-Methoden, die diesem Muster folgen müssen.  
  
## Regelbeschreibung  
 Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können.  Per Definition ist es nicht möglich, von einem versiegelten Typ zu erben. Dies bedeutet, dass geschützte Methoden auf versiegelten Typen nicht aufgerufen werden können.  
  
 Der C\#\-Compiler gibt bei diesem Fehler eine Warnung aus.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene des Members in privat, oder machen Sie den Typ erbbar.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Das Beibehalten des aktuellen Zustands des Typs kann Wartungsprobleme verursachen und bietet keine Vorteile.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]