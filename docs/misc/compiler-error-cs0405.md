---
title: "Compilerfehler CS0405 | Microsoft Docs"
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
  - "CS0405"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0405"
ms.assetid: 0bf51e24-dc6c-438f-a928-b5bfbf35f81a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0405
Doppelte "Einschränkung"\-Einschränkung für "Typparameter"\-Typparameter  
  
 Zwei der Einschränkungen in der generischen Deklaration sind identisch. Entfernen Sie das Duplikat, um den Fehler zu beheben.  
  
 Im folgenden Beispiel wird CS0405 generiert:  
  
```  
// CS0405.cs interface I { } class C<T> where T : I, I  // CS0405.cs { }  
```