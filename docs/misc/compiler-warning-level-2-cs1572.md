---
title: "Compilerwarnung (Stufe 2) CS1572 | Microsoft Docs"
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
  - "CS1572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1572"
ms.assetid: 24bc8b96-29d2-4201-bc4e-6b9b5a4f5a1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS1572
Der XML\-Kommentar für 'construct' enthält ein param\-Tag für 'Parameter', es gibt aber keinen Parameter mit diesem Namen.  
  
 Bei Verwendung der [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)\-Compileroption wurde ein Kommentar für einen Parameter angegeben, der für die Methode nicht vorhanden ist. Ändern Sie den an das Namensattribut übergebenen Wert, oder entfernen Sie eine der Kommentarzeilen.  
  
 Im folgenden Beispiel wird CS1572 generiert:  
  
```  
// CS1572.cs // compile with: /W:2 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <param name='Int1'>Used to indicate status.</param> /// <param name='Char1'>Used to indicate status.</param> /// <param name='Char2'>???</param> // CS1572 public static void MyMethod(int Int1, char Char1) { } /// <summary>help text</summary> public static void Main () { } }  
```