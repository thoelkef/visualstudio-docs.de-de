---
title: "Compilerfehler CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0418
'Klassenname': Eine abstrakte Klasse darf nicht versiegelt oder statisch sein.  
  
 Eine abstrakte Klasse kann nicht zum Erstellen von Objekten verwendet werden, sofern sie nicht abgeleitet wurde, daher ist die Versiegelung nicht sinnvoll. Eine abstrakte Klasse kann auch nicht sinnvollerweise statisch sein. Abstrakte Klassen dienen zur Unterstützung einer Objekthierarchie, die die abstrakte Klasse als Basis verwendet.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0418 generiert:  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```