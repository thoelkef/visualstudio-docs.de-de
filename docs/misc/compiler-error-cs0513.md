---
title: "Compilerfehler CS0513 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0513"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0513"
ms.assetid: 6f8569df-713d-4c9c-a675-6576dad139ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0513
"Funktion" ist abstrakt, ist aber in der nicht abstrakten Klasse "Klasse" enthalten  
  
 Eine Methode kann kein [abstrakter](/dotnet/csharp/language-reference/keywords/abstract) Member einer nicht abstrakten Klasse sein.  
  
 Im folgenden Beispiel wird CS0513 generiert:  
  
```  
// CS0513.cs namespace x { public class clx { abstract public void f();   // CS0513, abstract member of nonabstract class } }  
```