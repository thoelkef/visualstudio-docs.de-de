---
title: "Compilerfehler CS0524 | Microsoft Docs"
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
  - "CS0524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0524"
ms.assetid: a5cd8fb0-f5df-4580-9116-a6be4dffd1cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0524
„type“: Schnittstellen können keine Typen deklarieren.  
  
 Eine [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) darf keinen benutzerdefinierten Typ, sondern nur Methoden und Eigenschaften enthalten.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0524 generiert:  
  
```  
// CS0524.cs public interface Clx { public class Cly   // CS0524, delete user-defined type { } }  
  
```