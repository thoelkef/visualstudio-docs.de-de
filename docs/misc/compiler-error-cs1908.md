---
title: "Compilerfehler CS1908 | Microsoft Docs"
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
  - "CS1908"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1908"
ms.assetid: d7da31c2-48ef-4401-b885-3459b4d7f6f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1908
Der Typ des Arguments für das DefaultValue\-Attribut muss mit dem Parametertyp übereinstimmen.  
  
 Dieser Fehler wird generiert, wenn Sie ein falsches Argument als <xref:System.ComponentModel.DefaultValueAttribute>\-Attributwert verwenden. Verwenden Sie einen Wert, der mit dem Parametertyp übereinstimmt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1908 generiert.  
  
```  
// CS1908.cs // compile with: /target:library using System.Runtime.InteropServices; public interface ISomeInterface { void Bad([Optional] [DefaultParameterValue("true")] bool b);   // CS1908 void Good([Optional] [DefaultParameterValue(true)] bool b);   // OK }  
```