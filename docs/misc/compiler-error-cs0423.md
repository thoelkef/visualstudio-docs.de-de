---
title: "Compilerfehler CS0423 | Microsoft Docs"
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
  - "CS0423"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0423"
ms.assetid: e4ec44b6-bf9c-41f7-a309-8f8b9e325691
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0423
Da 'Klasse' das ComImport\-Attribut aufweist, muss 'Methode' extern oder abstrakt sein.  
  
 Die Angabe des ComImport\-Attributs impliziert, dass die Implementierung für die Klasse von einem COM\-Modul importiert werden muss. Weitere Methoden können nicht definiert werden.  
  
 Im folgenden Beispiel wird CS0423 generiert:  
  
```  
// CS0423.cs using System.Runtime.InteropServices; [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class ImageProperties { public static void Main()  // CS0423 { ImageProperties i = new ImageProperties(); } }  
```