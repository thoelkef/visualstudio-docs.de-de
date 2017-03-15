---
title: "Compilerwarnung (Stufe 2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS3019
Die CLS\-Kompatibilitätsprüfung wird nicht für 'Typ' durchgeführt \(ist außerhalb der Assembly nicht sichtbar\).  
  
 Diese Warnung tritt auf, wenn ein Typ oder Member mit dem <xref:System.CLSCompliantAttribute>\-Attribut für eine andere Assembly nicht sichtbar ist. Entfernen Sie das Attribut aus allen Klassen oder Membern, die für die andere Assembly nicht sichtbar sind, oder machen Sie den Typ bzw. die Member sichtbar, um diesen Fehler zu beheben. Weitere Informationen zur CLS\-Kompatibilität finden Sie unter [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
## Beispiel  
 Im folgenden Beispiel wird CS3019 generiert:  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## Siehe auch  
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)