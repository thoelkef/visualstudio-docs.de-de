---
title: "Compilerfehler CS0548 | Microsoft Docs"
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
  - "CS0548"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0548"
ms.assetid: c4d34da7-0b4a-4312-ac7f-46db100e43c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0548
'Eigenschaft': Die Eigenschaft oder der Indexer muss mindestens einen Accessor haben.  
  
 Eine Eigenschaft muss mindestens eine Accessormethode enthalten \('get' oder 'set'\).  
  
 Weitere Informationen finden Sie unter [Verwenden von Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0548 generiert:  
  
```  
// CS0548.cs // compile with: /target:library public class b { public int MyProp {}   // CS0548 public int MyProp2   // OK { get { return 0; } set {} } }  
```