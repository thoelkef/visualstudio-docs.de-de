---
title: "Compilerfehler CS0174 | Microsoft Docs"
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
  - "CS0174"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0174"
ms.assetid: c34c0fa4-d720-4dc5-b723-014203bab8f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0174
Für einen base\-Verweis ist eine Basisklasse erforderlich.  
  
 Dieser Fehler tritt nur dann auf, wenn die Common Language Runtime von .NET Framework den Quellcode für die `System.Object`\-Klasse kompiliert, die die einzige Klasse ist, für die keine Basisklasse vorhanden ist.