---
title: "Compilerfehler CS1032 | Microsoft Docs"
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
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1032
Die Definition von Präprozessorsymbolen kann nur vor dem ersten Token in der Datei vorgenommen\/aufgehoben werden.  
  
 Die `#define`\- und `#undef` [Präprozessordirektiven](/dotnet/csharp/language-reference/preprocessor-directives/index) müssen am Anfang eines Programms vor allen anderen Schlüsselwörtern verwendet werden, wie die in der Namespacedeklaration verwendeten Direktiven.  
  
 Im folgenden Beispiel wird CS1032 generiert:  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```