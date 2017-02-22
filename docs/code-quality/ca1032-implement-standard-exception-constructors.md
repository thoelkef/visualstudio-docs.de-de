---
title: "CA1032: Standardausnahmekonstruktoren implementieren | Microsoft Docs"
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
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1032: Standardausnahmekonstruktoren implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> und deklariert nicht alle erforderlichen Konstruktoren.  
  
## Regelbeschreibung  
 Ausnahmetypen müssen die folgenden Konstruktoren implementieren:  
  
-   NewException\(\) \(öffentlich\)  
  
-   NewException\(string\) \(öffentlich\)  
  
-   NewException\(string, Exception\) \(öffentlich\)  
  
-   NewException\(SerializationInfo, StreamingContext\) \(geschützt oder privat\)  
  
 Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert.  Der Konstruktor mit der Signatur `NewException(string, Exception)` wird z. B. zum Erstellen von Ausnahmen verwendet, die von anderen Ausnahmen verursacht werden.  Ohne diesen Konstruktor können Sie keine Instanz der benutzerdefinierten Ausnahme erstellen und auslösen, die eine innere \(geschachtelte\) Ausnahme enthält. Dies sollte in einer solchen Situation jedoch vom verwalteten Code geleistet werden.  Die ersten drei Ausnahmekonstruktoren sind stets öffentlich.  Der vierte Konstruktor ist in unversiegelten Klassen geschützt und privat in versiegelten Klassen.  Weitere Informationen finden Sie unter [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Ausnahme die fehlenden Konstruktoren hinzu, und stellen Sie sicher, dass sie die richtige Zugriffsebene aufweisen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Verstoß durch die Verwendung einer anderen Zugriffsebene für die öffentlichen Konstruktoren verursacht wird.  
  
## Beispiel  
 Das folgende Beispiel enthält einen Ausnahmetyp, der gegen diese Regel verstößt, und einen Ausnahmetyp, der ordnungsgemäß implementiert ist.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]