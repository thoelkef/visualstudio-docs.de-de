---
title: "CA1061: Basisklassenmethoden nicht ausblenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# CA1061: Basisklassenmethoden nicht ausblenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein abgeleiteter Typ deklariert eine Methode mit demselben Namen und derselben Anzahl an Parametern als eine seiner Basismethoden. Mindestens einer der Parameter ist ein Basistyp des entsprechenden Parameters in der Basismethode. Alle verbleibenden Parameter weisen Typen auf, die mit den entsprechenden Parametern in der Basismethode identisch sind.  
  
## Regelbeschreibung  
 Eine Methode in einem Basistyp wird durch eine Methode mit identischem Namen in einem abgeleiteten Typ verdeckt, wenn die Parametersignatur der abgeleiteten Methode sich nur hinsichtlich der Typen unterscheidet, die schwächer abgeleitet sind als die entsprechenden Typen in der Parametersignatur der Basismethode.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu behandeln, können Sie die Methode entfernen oder umbenennen oder die Parametersignatur so ändern, dass die Basismethode von der Methode nicht verdeckt wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]