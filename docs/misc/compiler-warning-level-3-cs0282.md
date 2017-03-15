---
title: "Compilerwarnung (Stufe 3) CS0282 | Microsoft Docs"
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
  - "CS0282"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0282"
ms.assetid: fd4cda5d-81c7-40e3-8424-c938b3447356
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0282
Es gibt keine festgelegte Reihenfolge für die Felder in mehreren Deklarationen der partiellen Klasse oder Struktur 'Typ'. Um eine Reihenfolge anzugeben, müssen sich alle Instanzenfelder in der gleichen Deklaration befinden.  
  
 Verlagern Sie alle Membervariablen in eine einzelne partielle Klassendefinition, um diesen Fehler zu beheben.  
  
 Dieser Fehler tritt häufig durch die Verwendung eines partiellen `struct`, das an mehreren Stellen definiert ist, wobei sich einige der Membervariablen in einer Definition und andere in einer anderen Definition befinden.  
  
 Durch den folgenden Code wird der Fehler CS0282 ausgelöst.  
  
## Beispiel  
 Dieser Code enthält eine Beschreibung für ein `struct`. Kompilieren Sie diese beiden Module mithilfe des folgenden Befehls gemeinsam in einem einzelnen Schritt:  
  
 `csc /targt:library cs0282_1.cs cs0282_2.cs`  
  
```  
partial struct A { int i; }  
```  
  
## Beispiel  
 Dieser Code enthält eine widersprüchliche Beschreibung für dasselbe `struct`.  
  
```  
partial struct A { int j; }  
```