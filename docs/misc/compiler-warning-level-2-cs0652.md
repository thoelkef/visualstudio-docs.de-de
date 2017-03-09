---
title: "Compilerwarnung (Stufe 2) CS0652 | Microsoft Docs"
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
  - "CS0652"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0652"
ms.assetid: 1ec1cee6-858a-4104-aa15-2668723c6331
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0652
Der Vergleich mit der ganzzahligen Konstante ist nutzlos; die Konstante befindet sich außerhalb des Bereichs vom Typ 'typ'  
  
 Der Compiler hat einen Vergleich zwischen einer Konstanten und einer Variablen erkannt, bei dem die Konstante außerhalb des Gültigkeitsbereichs der Variablen liegt.  
  
 Im folgenden Beispiel wird CS0652 generiert:  
  
```  
// CS0652.cs // compile with: /W:2 public class Class1 { private static byte i = 0; public static void Main() { short j = 256; if (i == 256)   // CS0652, 256 is out of range for byte i = 0; } }  
```