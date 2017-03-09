---
title: "Compilerfehler CS0061 | Microsoft Docs"
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
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0061
Inkonsistenter Zugriff: Auf die Basisschnittstelle 'interface 1' kann weniger zugegriffen werden als auf die Schnittstelle 'interface 2' .  
  
 Ein [public](/dotnet/csharp/language-reference/keywords/public)\-Konstrukt muss ein Objekt zurückgeben, auf das öffentlich zugegriffen werden kann.  
  
 Der Schnittstellenzugriff kann in einer abgeleiteten Schnittstelle nicht eingeschränkt werden. Weitere Informationen finden Sie unter [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index) und [Zugriffsmodifizierer](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 Das folgende Beispiel generiert CS0061:  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```