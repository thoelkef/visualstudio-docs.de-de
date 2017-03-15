---
title: "Compilerfehler CS1910 | Microsoft Docs"
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
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1910
Ein Argument vom Typ "Typ" ist für das DefaultValue\-Attribut nicht zutreffend.  
  
 Bei Parametern, deren Typ "Object" ist, muss das Argument für <xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> entweder `null`, ein ganzzahliger Typ, eine Gleitkommazahl, `bool`, `string`, `enum` oder `char` sein. Das Argument kann nicht den Typ <xref:System.Type> oder einen anderen Arraytyp aufweisen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1910 generiert:  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```