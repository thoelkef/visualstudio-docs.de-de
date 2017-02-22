---
title: "CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen | Microsoft Docs"
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
  - "CA1025"
  - "ReplaceRepetitiveArgumentsWithParamsArray"
helpviewer_keywords: 
  - "ReplaceRepetitiveArgumentsWithParamsArray"
  - "CA1025"
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über mehr als drei Parameter und die letzten drei Parameter sind vom gleichen Typ.  
  
## Regelbeschreibung  
 Verwenden Sie ein Parameterarray statt sich wiederholender Argumente, wenn die genaue Anzahl der Argumente nicht bekannt ist und diese Argumente vom gleichen Typ sind oder als gleicher Typ übergeben werden können.  Beispielsweise stellt die <xref:System.Console.WriteLine%2A>\-Methode eine allgemeine Überladung bereit, die ein Parameterarray verwendet, um eine beliebige Anzahl von <xref:System.Object>\-Argumenten zu akzeptieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen dieser Regel zu beheben, ersetzen Sie die wiederholten Argumente durch ein Parameterarray.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann immer gefahrlos unterdrückt werden. Diese Konzeption kann jedoch Probleme hinsichtlich der Verwendbarkeit verursachen.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-cs[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]