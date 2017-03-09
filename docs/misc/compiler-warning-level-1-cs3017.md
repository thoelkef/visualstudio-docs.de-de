---
title: "Compilerwarnung (Stufe 1) CS3017 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3017
Das CLSCompliant\-Attribut kann nicht für ein Modul angegeben werden, das sich vom CLSCompliant\-Attribut der Assembly unterscheidet.  
  
 Diese Warnung tritt auf, wenn ein CLSCompliant\-Assemblyattribut vorhanden ist, das im Konflikt mit einem CLSCompliant\-Modulattribut steht. Eine Assembly, die CLS\-kompatibel ist, kann nicht Module enthalten, die nicht CLS\-kompatibel sind. Um diese Warnung zu beheben, achten Sie darauf, dass die CLSCompliant\-Assembly\- und Modulattribute entweder beide True oder beide False sind, oder Entfernen eins der Attribute. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS3017 generiert:  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```