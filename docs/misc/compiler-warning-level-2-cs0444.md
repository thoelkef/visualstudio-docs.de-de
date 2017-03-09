---
title: "Compilerwarnung (Stufe 2) CS0444 | Microsoft Docs"
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
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0444
Der vordefinierte Typ 'typname 1' wurde in 'System\-Namespace 1' nicht gefunden, wohl aber in 'System\-Namespace 2'.  
  
 Ein vordefiniertes Objekt, wie etwa <xref:System.Int32>, wurde nicht gefunden, wo es vom Compiler erwartet wurde, stattdessen in 'System\-Namespace 2'.  
  
 Der Fehler ist möglicherweise ein Hinweis auf eine nicht ordnungsgemäße Installation von .NET Framework. Installieren Sie .NET Framework erneut, um das Problem zu beheben.  
  
 Dieser Fehler kann auch beim Erstellen eigener Basisklassenbibliotheken auftreten. Erstellen Sie in diesem Fall „mscorlib“ erneut, um den Fehler zu beheben.