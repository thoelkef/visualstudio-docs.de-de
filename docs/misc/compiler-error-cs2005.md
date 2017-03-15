---
title: "Compilerfehler CS2005 | Microsoft Docs"
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
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2005
Fehlende Dateispezifikation für die Option "Option".  
  
 Eine [Compileroption](/dotnet/csharp/language-reference/compiler-options/index) wurde nur teilweise angegeben.  
  
 Bei Verwendung von [\/recurse](/dotnet/csharp/language-reference/compiler-options/recurse-compiler-option) müssen Sie beispielsweise die zu durchsuchende Datei angeben: **\/recurse:***Dateiname***cs**.  
  
## Beispiel  
 Im folgenden Beispiel wird CS2005 generiert.  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```