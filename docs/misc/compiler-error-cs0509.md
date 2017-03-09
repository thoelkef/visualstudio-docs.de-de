---
title: "Compilerfehler CS0509 | Microsoft Docs"
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
  - "CS0509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0509"
ms.assetid: dc113e03-7a01-489b-b886-51ee056fc96a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0509
'klasse1': Ableitung vom versiegelten Typ 'klasse2' nicht möglich  
  
 Eine [versiegelte](/dotnet/csharp/language-reference/keywords/sealed) Klasse kann nicht als [Basisklasse](/dotnet/csharp/language-reference/keywords/base) dienen. Strukturen sind standardmäßig versiegelt.  
  
 Im folgenden Beispiel wird CS0509 generiert:  
  
```  
// CS0509.cs // compile with: /target:library sealed public class clx {} public class cly : clx {}   // CS0509  
```