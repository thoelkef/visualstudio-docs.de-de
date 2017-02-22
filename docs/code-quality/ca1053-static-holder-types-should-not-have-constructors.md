---
title: "CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen | Microsoft Docs"
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
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor.  
  
## Regelbeschreibung  
 Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist.  Da der Typ außerdem keine nicht statischen Member besitzt, wird durch die Erstellung einer Instanz kein Zugriff auf einen Member des Typs erteilt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Standardkonstruktor, oder definieren Sie ihn als privaten Konstruktor.  
  
> [!NOTE]
>  Einige Compiler erstellen automatisch einen öffentlichen Standardkonstruktor, wenn der Typ keine Konstruktoren definiert.  Trifft dies auf Ihren Typ zu, fügen Sie einen private\-Standardkonstruktor hinzu, um den Verstoß zu beseitigen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Das Vorhandensein des Konstruktors impliziert, dass es sich bei dem Typ nicht um einen statischen Typ handelt.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  Beachten Sie, dass es im Quellcode keinen Standardkonstruktor gibt.  Wenn dieser Code in eine Assembly kompiliert wird, fügt der C\#\-Compiler einen Standardkonstruktor ein, der gegen diese Regel verstößt.  Um diesen Verstoß zu beheben, deklarieren Sie einen privaten Konstruktor.  
  
 [!code-cs[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]