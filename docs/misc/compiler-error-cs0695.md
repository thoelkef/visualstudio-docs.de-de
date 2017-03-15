---
title: "Compilerfehler CS0695 | Microsoft Docs"
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
  - "CS0695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0695"
ms.assetid: 05f6c8cf-6147-4ac7-84ea-e1f34f8ef9f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0695
"Generischer Typ" kann nicht gleichzeitig "generische Schnittstelle" und "generische Schnittstelle" implementieren, da diese für einige Typparameterersetzungen zusammengeführt werden können.  
  
 Dieser Fehler tritt auf, wenn eine generische Klasse mehrere Parametrisierungen derselben generischen Schnittstelle implementiert und eine Ersetzung von Typparametern vorhanden ist, durch die die beiden Schnittstellen als identisch festgelegt werden. Implementieren Sie nur eine der Schnittstellen, um diesen Fehler zu vermeiden, oder ändern Sie die Typparameter, sodass kein Konflikt mehr vorliegt.  
  
 Im folgenden Beispiel wird CS0695 generiert:  
  
```  
// CS0695.cs // compile with: /target:library interface I<T> { } class G<T1, T2> : I<T1>, I<T2>  // CS0695 { }  
```