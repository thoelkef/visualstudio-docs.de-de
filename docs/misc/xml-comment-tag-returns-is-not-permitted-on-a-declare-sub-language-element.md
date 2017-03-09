---
title: "Das XML-Kommentartag &quot;returns&quot; ist f&#252;r ein &quot;declare sub&quot;-Sprachelement nicht zul&#228;ssig. | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das XML-Kommentartag &quot;returns&quot; ist f&#252;r ein &quot;declare sub&quot;-Sprachelement nicht zul&#228;ssig.
Das XML\-Kommentartag "returns" ist für ein "declare sub"\-Sprachelement nicht zulässig. Der XML\-Kommentar wird ignoriert.  
  
 Ein XML\-Kommentar für eine `Declare Sub`\-Deklaration darf kein `<`returns`>`\-Tag enthalten.  
  
 **Fehler\-ID:** BC42315  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das nicht unterstützte `<`returns`>`\-Tag.  
  
## Siehe auch  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documenting Your Code with XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)