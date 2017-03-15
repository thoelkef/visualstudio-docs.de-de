---
title: "CA2222: Sichtbarkeit f&#252;r geerbte Member nicht verringern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2222: Sichtbarkeit f&#252;r geerbte Member nicht verringern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine private Methode in einem unversiegelten Typ besitzt eine Signatur, die mit derjenigen einer öffentlichen Methode übereinstimmt, die in einem Basistyp deklariert ist.  Die private Methode ist nicht final.  
  
## Regelbeschreibung  
 Sie sollten den Zugriffsmodifizierer für geerbte Member nicht ändern.  Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert.  Wenn der Member zu einem privaten gemacht wird und der Typ unversiegelt ist, können erbende Typen die letzte öffentliche Implementierung der Methode in der Vererbungshierarchie aufrufen.  Wenn Sie den Zugriffsmodifizierer ändern müssen, muss entweder die Methode als final gekennzeichnet werden, oder ihr Typ muss versiegelt werden, um ein Überschreiben der Methode zu verhindern.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, ändern Sie den Zugriff in nicht\-privat.  Sie haben aber auch die Möglichkeit, die Methode zu einer final\-Methode zu machen, wenn die von Ihnen verwendete Programmiersprache dies unterstützt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]