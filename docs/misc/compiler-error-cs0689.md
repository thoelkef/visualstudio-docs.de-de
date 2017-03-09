---
title: "Compilerfehler CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0689
Eine Ableitung von 'identifier' ist nicht möglich, da es sich um einen Typparameter handelt  
  
 Die Angabe von Basisklassen oder Schnittstellen für generische Klassen kann nicht durch einen Typparameter erfolgen. Nehmen Sie stattdessen eine Ableitung von einer spezifischen Klasse oder Schnittstelle oder einer spezifischen generischen Klasse vor, oder schließen Sie den unbekannten Typ als Member ein.  
  
 Im folgenden Beispiel wird CS0689 generiert:  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```