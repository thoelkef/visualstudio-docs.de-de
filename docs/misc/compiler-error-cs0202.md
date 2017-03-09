---
title: "Compilerfehler CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0202
Für "foreach" muss der Rückgabetyp "Typ" von "'type.GetEnumerator\(\)" über eine passende öffentliche MoveNext\-Methode und eine öffentliche Current\-Eigenschaft verfügen.  
  
 Eine <xref:System.Collections.IEnumerable.GetEnumerator%2A>\-Funktion, die zur Aktivierung der Verwendung von foreach\-Anweisungen verwendet wird, kann weder einen Zeiger noch ein Array zurückgeben. Sie muss eine Instanz einer Klasse zurückgeben, die als Enumerator agieren kann. Die Anforderungen an einen Enumerator schließen eine öffentliche Current\-Eigenschaft und eine öffentliche MoveNext\-Methode ein.  
  
> [!NOTE]
>  In C\# 2.0 werden Current und MoveNext vom Compiler automatisch generiert. Weitere Informationen finden Sie im Codebeispiel unter [Generische Schnittstellen](/dotnet/csharp/programming-guide/generics/generic-interfaces).  
  
 Im folgenden Beispiel wird CS0202 generiert:  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```