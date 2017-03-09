---
title: "Compilerfehler CS0723 | Microsoft Docs"
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
  - "CS0723"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0723"
ms.assetid: b9f6aebc-e959-407d-8d5c-6a6dcabcfe0f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0723
Die Variable des statischen Typs 'Typ' kann nicht deklariert werden.  
  
 Instanzen von statischen Typen können nicht erstellt werden.  
  
 Im folgenden Beispiel wird CS0723 generiert:  
  
```  
// CS0723.cs public static class SC { } public class CMain { public static void Main() { SC sc = null;  // CS0723 } }  
```