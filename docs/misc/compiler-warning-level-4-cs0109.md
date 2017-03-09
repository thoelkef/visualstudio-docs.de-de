---
title: "Compilerwarnung (Stufe 4) CS0109 | Microsoft Docs"
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
  - "CS0109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0109"
ms.assetid: 42ac72e5-5081-4e8b-b2cf-5e10c1606676
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 4) CS0109
Der Member "Member" blendet einen vererbten Member nicht aus. Das New\-Schlüsselwort ist nicht erforderlich  
  
 Eine Klassendeklaration enthält das [New](/dotnet/csharp/language-reference/keywords/new)\-Schlüsselwort, obwohl die Deklaration eine bestehende Deklaration in einer Basisklasse nicht überschreibt. Sie können das **New**\-Schlüsselwort löschen.  
  
 Im folgenden Beispiel wird CS0109 generiert:  
  
```  
// CS0109.cs // compile with: /W:4 namespace x { public class a { public int i; } public class b : a { public new int i; public new int j;   // CS0109 public static void Main() { } } }  
```