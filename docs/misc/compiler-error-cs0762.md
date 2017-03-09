---
title: "Compilerfehler CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0762
Auf der Grundlage der Methode "Methode" kann kein Delegat erstellt werden, da es sich um eine partielle Methode ohne implementierende Deklaration handelt.  
  
 Für eine partielle Methode ist keine implementierende Deklaration erforderlich. Für einen Delegaten ist es jedoch erforderlich, dass die gekapselte Methode über eine Implementierung verfügt.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie eine Implementierung für die Methode bereit, die zur Initialisierung des Delegaten verwendet wird.  
  
## Beispiel  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```