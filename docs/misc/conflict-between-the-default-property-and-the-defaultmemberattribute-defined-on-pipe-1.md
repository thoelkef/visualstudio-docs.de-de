---
title: "Konflikt zwischen der Standardeigenschaft und &quot;DefaultMemberAttribute&quot; (definiert in &quot;|1&quot;). | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Konflikt zwischen der Standardeigenschaft und &quot;DefaultMemberAttribute&quot; (definiert in &quot;|1&quot;).
Eine Klasse, Struktur oder Schnittstelle deklariert mit dem [Default](/dotnet/visual-basic/language-reference/modifiers/default)\-Schlüsselwort eine Standardeigenschaft, wendet jedoch auch <xref:System.Reflection.DefaultMemberAttribute> an, um einen anderen Member als Standardmember festzulegen.  
  
 Ein Typ kann höchstens über einen Standardmember verfügen. Wenn Sie eine Standardeigenschaft deklarieren, wendet Visual Basic automatisch <xref:System.Reflection.DefaultMemberAttribute> auf die Klasse, Struktur oder Schnittstelle an, die diese Eigenschaft definiert.  
  
 **Fehler\-ID:** BC32304  
  
### So beheben Sie diesen Fehler  
  
1.  Entscheiden Sie, welcher Member der Standardmember der Klasse, Struktur oder Schnittstelle sein soll.  
  
2.  Entfernen Sie die widersprüchliche Deklaration \(entweder das `Default`\-Schlüsselwort oder <xref:System.Reflection.DefaultMemberAttribute>\).  
  
## Siehe auch  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)   
 [NICHT IM BUILD: Standardeigenschaften](http://msdn.microsoft.com/de-de/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)