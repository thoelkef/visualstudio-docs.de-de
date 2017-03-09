---
title: "Compilerwarnung (Stufe 2) CS3021 | Microsoft Docs"
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
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS3021
"Typ" erfordert kein CLSCompliant\-Attribut, da die Assembly kein CLSCompliant\-Attribut aufweist.  
  
 Diese Warnung tritt auf, wenn `[CLSCompliant(false)]`  bei einer Klasse in einer Assembly angegeben ist, für die das Attribut "CLSCompliant" auf Assemblyebene nicht auf true festgelegt ist \(also die Zeile `[assembly: CLSCompliant(true)]` fehlt\). Da sich die Assembly nicht selbst als CLS\-kompatibel deklariert, besteht keine Notwendigkeit, dass sich ein Element in der Assembly selbst als nicht kompatibel deklariert, da angenommen wird, dass keine Kompatibilität besteht. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 Damit diese Warnung nicht mehr angezeigt wird, entfernen Sie das Attribut, oder fügen Sie das Attribut auf Assemblyebene hinzu.  
  
## Beispiel  
 Im folgenden Beispiel wird CS3021 generiert.  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## Siehe auch  
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)