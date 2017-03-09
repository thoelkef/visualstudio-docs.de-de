---
title: "Compilerfehler CS0430 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0430
Der externe Alias 'Alias' wurde nicht in einer \/reference\-Option angegeben.  
  
 Dieser Fehler tritt auf, wenn der externe Alias gefunden wurde, aber kein Alias als Verweis in der Befehlszeile angegeben wurde. Um den Fehler CS0430 zu beheben, kompilieren Sie mit **\/reference**.  
  
## Beispiel  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## Beispiel  
 Beim Kompilieren mit **\/reference:MyType\=cs0430\_a.dll** um auf die im vorherigen Beispiel erstellte DLL zu verweisen, wird dieser Fehler behoben. Im folgenden Beispiel wird CS0430 generiert:  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```