---
title: "Compilerfehler CS1665 | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1665
Puffer fester Größe müssen länger als 0 \(null\) sein.  
  
 Dieser Fehler tritt auf, wenn ein Puffer mit fester Größe mit einer Größe null oder mit negativer Größe deklariert wird. Die Länge eines Puffers mit fester Größe muss eine positive ganze Zahl sein.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1665 generiert:  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```