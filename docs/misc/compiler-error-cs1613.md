---
title: "Compilerfehler CS1613 | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1613
Die verwaltete Co\-Klassen\-Wrapperklasse "class" für die "interface"\-Schnittstelle kann nicht gefunden werden. \(Möglicherweise fehlt ein Assemblyverweis.\)  
  
 Es wurde versucht, ein COM\-Objekt über eine Schnittstelle zu instanziieren. Die Schnittstelle verfügt über das **ComImport**\- und das `CoClass`\-Attribut, aber der Compiler kann nicht den Typ für das `CoClass`\-Attribut finden.  
  
 Um diesen Fehler zu beheben, können Sie eine der folgenden Lösungen versuchen:  
  
-   Fügen Sie einen Verweis auf die Assembly hinzu, die die Co\-Klasse aufweist \(in den meisten Fällen sollten sich die Schnittstelle und die Co\-Klasse in der gleichen Assembly befinden\). Informationen finden Sie unter [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) oder [Dialogfeld "Verweis hinzufügen"](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7).  
  
-   Korrigieren Sie das `CoClass`\-Attribut in der Schnittstelle.  
  
 Das folgende Beispiel veranschaulicht die richtige Verwendung von **CoClassAttribute**:  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```