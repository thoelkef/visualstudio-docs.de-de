---
title: "Compilerfehler CS1679 | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1679
Ungültiger externer Alias für '\/reference'; 'Bezeichner' ist kein gültiger Bezeichner.  
  
 Wenn Sie das Aliasfeature der externen Assembly der **\/reference**\-Option verwenden, muss der auf **\/reference:** folgende und „\=“ voranstehende Text ein gültiger C\#\-Bezeichner oder ein Schlüsselwort gemäß der C\#\-Programmiersprachenspezifikation sein.  
  
 Ändern Sie den Text vor dem „\=“ in einen gültigen C\#\-Bezeichner oder ein C\#\-Schlüsselwort, um diesen Fehler zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1679 generiert:  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```