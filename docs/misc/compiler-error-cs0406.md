---
title: "Compilerfehler CS0406 | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0406
Die Klassentypeinschränkung 'constraint' muss vor allen anderen Einschränkungen stehen  
  
 Wenn ein generischer Typ oder eine generische Methode Klassentypeinschränkungen aufweist, muss diese Einschränkung zuerst aufgeführt werden. Um diesen Fehler zu vermeiden, verschieben Sie die Klassentypeinschränkung an den Anfang der Einschränkungsliste.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0406 generiert.  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```