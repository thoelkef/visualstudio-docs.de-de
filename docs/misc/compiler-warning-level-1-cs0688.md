---
title: "Compilerwarnung (Stufe 1) CS0688 | Microsoft Docs"
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
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0688
"Methode1" hat einen Linkaufruf, überschreibt bzw. implementiert aber "Methode2", die keinen Linkaufruf enthält. Möglicherweise besteht eine Sicherheitslücke.  
  
 Der für die Methode der abgeleiteten Klasse eingerichtete Linkaufruf kann einfach umgangen werden, indem die Methode der Basisklasse aufgerufen wird. Um die Sicherheitslücke zu schließen, muss die Methode der Basisklasse den Linkaufruf ebenfalls verwenden. Weitere Informationen finden Sie unter [Demand und LinkDemand](http://msdn.microsoft.com/de-de/1ab877f2-70f4-4e0d-8116-943999dfe8f5).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0688 generiert. Um die Warnung aufzulösen, ohne die Basisklasse zu ändern, entfernen Sie das Sicherheitsattribut aus der überschreibenden Methode. Das Sicherheitsproblem wird dadurch nicht behoben.  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```