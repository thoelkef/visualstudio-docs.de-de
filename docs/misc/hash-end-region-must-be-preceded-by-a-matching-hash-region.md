---
title: "&#39;#End Region&#39; muss ein entsprechendes &#39;#Region&#39; voranstehen. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; muss ein entsprechendes &#39;#Region&#39; voranstehen.
Mit `#Region` können Sie einen Codeblock festlegen, der bei Verwendung der Gliederungsfunktion des Code\-Editors von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erweitert oder reduziert werden kann. Start und Ende von `#Region`\-Anweisungen müssen sich im gleichen Codeblock befinden.  
  
 **Fehler\-ID:** BC30680  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie `#Region` an der passenden Position vor der entsprechenden `#End` `Region`\-Anweisung ein.  
  
## Siehe auch  
 [\#Region Directive](/dotnet/visual-basic/language-reference/directives/region-directive)