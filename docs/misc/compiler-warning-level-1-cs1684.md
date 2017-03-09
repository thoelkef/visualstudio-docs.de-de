---
title: "Compilerwarnung (Stufe 1) CS1684 | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1684
Der Verweis auf Typ 'Typname' wurde angeblich in 'Namespace' deklariert, konnte jedoch nicht gefunden werden.  
  
 Dieser Fehler kann durch einen Verweis innerhalb eines Namespace verursacht werden, der auf einen Typ verweist, der angeblich in einem zweiten Namespace vorhanden ist, wobei der Typ jedoch nicht existiert. Laut der Datei „mydll.dll“ befindet sich z. B. der Typ `A` in der Datei „yourdll.dll“, aber dieser Typ ist in der Datei nicht vorhanden. Eine mögliche Ursache für diesen Fehler ist, dass die Version der verwendeten Datei „yourdll.dll“ veraltet ist und `A` noch nicht definiert wurde.  
  
 Im folgenden Beispiel wird CS1684 generiert.  
  
## Beispiel  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## Beispiel  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## Beispiel  
 Wir erstellen nun die erste Assembly neu, wobei die Definition der Klasse C2 ausgelassen wird, die bei der Neukompilierung nicht definiert wird.  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## Beispiel  
 Dieses Modul verweist mithilfe des Bezeichners `Ref` auf das zweite Modul. Das zweite Modul enthält jedoch einen Verweis auf die Klasse `C2`, die aufgrund der Kompilierung im vorherigen Schritt nicht mehr vorhanden ist. Daher wird die Fehlermeldung CS1684 bei der Kompilierung dieses Moduls zurückgegeben.  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```