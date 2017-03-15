---
title: "Compilerwarnung (Stufe 1) CS0809 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0809
Der veraltete Member 'MemberA' überschreibt den nicht veralteten Member 'MemberB'.  
  
 In der Regel sollte ein als veraltet gekennzeichneter Member keinen Member überschreiben, der nicht als veraltet gekennzeichnet ist. Diese Warnung wird in [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], jedoch nicht in [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] generiert.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das `Obsolete`\-Attribut aus dem überschreibenden Member, oder fügen Sie es zum Basisklassenmember hinzu.  
  
## Beispiel  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```