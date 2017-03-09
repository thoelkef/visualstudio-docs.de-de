---
title: "Compilerwarnung (Stufe 2) CS1571 | Microsoft Docs"
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
  - "CS1571"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1571"
ms.assetid: 23b08885-9f69-4376-a952-4820b065a5c0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1571
Der XML\-Kommentar für 'Konstrukt' enthält ein doppeltes typeparam\-Tag für 'Parameter'.  
  
 Bei Verwendung der [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)\-Compileroption wurden mehrere Kommentare für denselben Methodenparameter gefunden. Entfernen Sie eine der doppelten Zeilen.  
  
 Im folgenden Beispiel wird CS1571 generiert:  
  
```  
// CS1571.cs // compile with: /W:2 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <param name='Int1'>Used to indicate status.</param> /// <param name='Char1'>An initial.</param> /// <param name='Int1'>Used to indicate status.</param> // CS1571 public static void MyMethod(int Int1, char Char1) { } /// <summary>help text</summary> public static void Main () { } }  
```