---
title: "Compilerfehler CS1557 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1557
"Klasse" befindet sich in einer anderen Ausgabedatei und kann daher nicht für die Main\-Methode verwendet werden.  
  
 Die [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)\-Compileroption wurde für eine Ausgabedatei in einer Kompilierung mit mehreren Ausgabedateien angegeben. Die Klasse wurde aber nicht im Quellcode für die \/main\-Kompilierung gefunden, sondern sie wurde in einer Quellcodedatei für eine der anderen Ausgabedateien der Kompilierung gefunden.