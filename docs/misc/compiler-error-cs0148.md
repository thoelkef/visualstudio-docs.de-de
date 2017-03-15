---
title: "Compilerfehler CS0148 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0148"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0148"
ms.assetid: d199afbf-02e1-4a1c-9e36-07bf86f1a2fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0148
Der Delegat "Delegat" hat keinen gültigen Konstruktor.  
  
 Sie haben ein verwaltetes Programm \(das die Common Language Runtime von .NET Framework verwendet\) importiert und verwendet, das mit einem anderen Compiler erstellt wurde. Dieser Compiler hat einen falsch formatierten [Delegaten](/dotnet/csharp/language-reference/keywords/delegate)konstruktor zugelassen. Weitere Informationen finden Sie unter [Delegaten](/dotnet/csharp/programming-guide/delegates/index).