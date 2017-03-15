---
title: "Compilerfehler CS0200 | Microsoft Docs"
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
  - "CS0200"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0200"
ms.assetid: 1990704a-edfa-4dbd-8477-d9c7aae58c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0200
Einer Eigenschaft oder einem Indexer "Eigenschaft" kann nichts zugewiesen werden \-\- sie sind schreibgeschützt.  
  
 Es wurde versucht, einer [Eigenschaft](/dotnet/csharp/programming-guide/classes-and-structs/using-properties) einen Wert zuzuweisen, aber die Eigenschaft hat keinen set\-Accessor. Beheben Sie den Fehler, indem Sie einen set\-Accessor hinzufügen. Weitere Informationen finden Sie unter [Gewusst wie: Deklarieren und Verwenden von Lese\-\/Schreibeigenschaften](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20\(C%23%20Programming%20Guide\).md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0200 generiert:  
  
```  
// CS0200.cs public class MainClass { // private int _mi; int I { get { return 1; } // uncomment the set accessor and declaration for _mi /* set { _mi = value; } */ } public static void Main () { MainClass II = new MainClass(); II.I = 9;   // CS0200 } }  
```