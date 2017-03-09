---
title: "Compilerfehler CS0533 | Microsoft Docs"
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
  - "CS0533"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0533"
ms.assetid: f8b38c5a-d365-4081-a101-6282bdd19069
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0533
'Member der abgeleiteten Klasse' blendet den geerbten abstrakten Member 'Basisklassenmember' aus.  
  
 Eine [Basisklassenmethode](/dotnet/csharp/language-reference/keywords/class) wird ausgeblendet. Überprüfen Sie die Syntax der Deklaration, um festzustellen, ob diese fehlerfrei ist.  
  
 Weitere Informationen finden Sie unter [base](/dotnet/csharp/language-reference/keywords/base).  
  
 Im folgenden Beispiel wird CS0533 generiert:  
  
```  
// CS0533.cs namespace x { abstract public class a { abstract public void f(); } abstract public class b : a { new abstract public void f();   // CS0533 // try the following lines instead // override public void f() // { // } public static void Main() { } } }  
```