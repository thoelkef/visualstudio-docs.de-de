---
title: "Compilerfehler CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0250
Rufen Sie die Finalize\-Methode der Basisklasse nicht direkt auf. Sie wird vom Destruktor automatisch aufgerufen.  
  
 Ein Programm kann nicht versuchen, die Bereinigung von Ressourcen der Basisklasse zu erzwingen.  
  
 Weitere Informationen finden Sie unter [Finalize\-Methoden und Destruktoren](http://msdn.microsoft.com/de-de/fd376774-1643-499b-869e-9546a3aeea70).  
  
 Im folgenden Beispiel wird CS0250 generiert:  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```