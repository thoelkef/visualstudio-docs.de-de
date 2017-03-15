---
title: "Das Conditional-Attribut ist nur in Sub-Deklarationen g&#252;ltig. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41007"
  - "vbc41007"
helpviewer_keywords: 
  - "BC41007"
ms.assetid: 36554e18-dac6-4bed-bdd0-f0819a3a288e
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Conditional-Attribut ist nur in Sub-Deklarationen g&#252;ltig.
Das <xref:System.Diagnostics.ConditionalAttribute>\-Attribut wurde auf eine andere Methodendeklaration als eine `Sub`\-Prozedur angewendet.  
  
 **Fehler\-ID:** BC41007  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie <xref:System.Diagnostics.ConditionalAttribute> aus der ungültigen Deklaration.  
  
## Siehe auch  
 <xref:System.Diagnostics.ConditionalAttribute>   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)