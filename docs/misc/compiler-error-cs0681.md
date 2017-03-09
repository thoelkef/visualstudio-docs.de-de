---
title: "Compilerfehler CS0681 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0681
Der Modifizierer 'abstract' ist für Felder nicht gültig. Verwenden Sie stattdessen eine Eigenschaft.  
  
 Ein Feld kann nicht als abstrakt definiert werden. Sie können jedoch eine abstrakte Eigenschaft verwenden, die auf das Feld zugreift.  
  
## Beispiel  
 Das folgende Beispiel generiert CS0681:  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## Beispiel  
 Verwenden Sie stattdessen den folgenden Code:  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```