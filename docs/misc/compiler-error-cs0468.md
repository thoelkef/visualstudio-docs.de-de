---
title: "Compilerfehler CS0468 | Microsoft Docs"
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
  - "CS0468"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0468"
ms.assetid: 1ec4f8af-0b32-4ea9-8bc0-bb9e52b9457b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0468
Mehrdeutigkeit zwischen Typ 'typ1' und Typ 'typ2'  
  
 Dieser Fehler wird generiert, wenn in der zu kompilierenden Assembly zwei Typen vorhanden sind, die den gleichen vollqualifizierten Namen aufweisen. Die kann beispielsweise auftreten, wenn sich beide in hinzugefügten Modulen befinden oder einer in einem hinzugefügten Modul und der andere im Quellcode vorkommt.