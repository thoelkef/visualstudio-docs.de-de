---
title: "Compilerwarnung (Stufe 1) CS3014 | Microsoft Docs"
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
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3014
"Member" erfordert kein CLSCompliant\-Attribut, da die Assembly kein CLSCompliant\-Attribut aufweist.  
  
 In einer Quellcodedatei, in der keine Kompatibilität mit der Common Language Specification \(CLS\) angegeben wurde, war ein Konstrukt in der Datei als CLS\-kompatibel markiert. Dies ist nicht zulässig. Um diese Warnung zu beheben, fügen Sie der Datei ein CLS\-kompatibles Attribut auf Assemblyebene hinzu \(kommentieren Sie im folgenden Beispiel die Zeile aus, die das Attribut auf Assemblyebene enthält\). Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3) und [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3014 generiert:  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```