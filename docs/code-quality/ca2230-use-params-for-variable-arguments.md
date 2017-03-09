---
title: "CA2230: params f&#252;r Variablenargumente verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: params f&#252;r Variablenargumente verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die die `VarArgs`\-Aufrufkonvention verwendet.  
  
## Regelbeschreibung  
 Die `VarArgs`\-Aufrufkonvention wird in bestimmten Methodendefinitionen verwendet, die eine variable Anzahl von Parametern übernehmen.  Methoden, die die `VarArgs`\-Aufrufkonvention verwenden, sind nicht CLS\-kompatibel, und möglicherweise kann nicht in allen Programmiersprachen darauf zugegriffen werden.  
  
 In C\# wird die `VarArgs`\-Aufrufkonvention verwendet, wenn die Parameterliste einer Methode mit dem `__arglist`\-Schlüsselwort endet.  Visual Basic unterstützt die `VarArgs`\-Aufrufkonvention nicht, und Visual C\+\+ lässt ihre Verwendung nur in nicht verwaltetem Code zu, in dem die Auslassungsnotation `...` verwendet wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß dieser Regel in C\# zu beheben, verwenden Sie statt `__arglist` das [params](/dotnet/csharp/language-reference/keywords/params)\-Schlüsselwort.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Methoden veranschaulicht: eine Methode, die gegen die Regel verstößt, und eine Regel, die der Regel entspricht.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## Siehe auch  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)