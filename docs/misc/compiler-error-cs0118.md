---
title: "Compilerfehler CS0118 | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0118
"Konstrukt1\_Name" ist ein "Konstrukt1", wird aber wie ein "Konstrukt2" verwendet.  
  
 Der Compiler hat eine Situation festgestellt, bei der ein Konstrukt fehlerhaft verwendet bzw. eine unzulässiger Vorgang für ein Konstrukt versucht wurde. Häufige Ursachen für diesen Fehler sind z. B.:  
  
-   Es wurde versucht, einen Namespace \(statt einer Klasse\) zu instanziieren.  
  
-   Es wurde versucht, ein Feld \(statt einer Methode\) aufzurufen.  
  
-   Es wurde versucht, einen Typ als Variable zu verwenden.  
  
-   Es wurde versucht, einen externen Alias als Typ zu verwenden.  
  
 Um diesen Fehler zu beheben, müssen Sie sicherstellen, dass der ausgeführte Vorgang für den Typ, für den der Vorgang ausgeführt wird, gültig ist.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0118 generiert.  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```