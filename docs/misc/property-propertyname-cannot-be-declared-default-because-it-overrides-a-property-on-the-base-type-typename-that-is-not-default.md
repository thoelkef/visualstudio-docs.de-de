---
title: "Die Eigenschaft &#39;&lt;eigenschaftsname&gt;&#39; kann nicht als &#39;Default&#39; erkl&#228;rt werden, da sie eine Eigenschaft des Basis&lt;typ&gt;s &#39;&lt;typname&gt;&#39; &#252;berschreibt, die ihrerseits keinen Standardwert darstellt | Microsoft Docs"
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
  - "bc30504"
  - "vbc30504"
helpviewer_keywords: 
  - "BC30504"
ms.assetid: af5d55b7-80bc-4085-8fcf-01d8acbe9290
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Eigenschaft &#39;&lt;eigenschaftsname&gt;&#39; kann nicht als &#39;Default&#39; erkl&#228;rt werden, da sie eine Eigenschaft des Basis&lt;typ&gt;s &#39;&lt;typname&gt;&#39; &#252;berschreibt, die ihrerseits keinen Standardwert darstellt
Sie haben versucht, eine Eigenschaft als `Default` zu deklarieren, die keine gültige Deklaration darstellt, da sie eine Eigenschaft überschreibt, die in der Basisklasse nicht als `Default` deklariert wurde.  
  
 **Fehler\-ID:** BC30504  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Default`\-Deklaration.  
  
## Siehe auch  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)