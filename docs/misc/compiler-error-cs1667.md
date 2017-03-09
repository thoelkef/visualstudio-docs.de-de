---
title: "Compilerfehler CS1667 | Microsoft Docs"
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
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1667
Das Attribut 'attribute' ist in Zugriffsmethoden von Eigenschaften oder Ereignissen ungültig. Es ist nur in Deklarationen vom Typ 'declaration type' gültig.  
  
 Dieser Fehler tritt auf, wenn Sie ein Attribut für die Zugriffsmethode einer Eigenschaft oder eines Ereignisses verwenden, das sich jedoch auf die Eigenschaft oder das Ereignis selbst bezieht. Dieser Fehler kann bei den Attributen <xref:System.CLSCompliantAttribute>, <xref:System.Diagnostics.ConditionalAttribute> und <xref:System.ObsoleteAttribute> auftreten.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1670 generiert:  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```