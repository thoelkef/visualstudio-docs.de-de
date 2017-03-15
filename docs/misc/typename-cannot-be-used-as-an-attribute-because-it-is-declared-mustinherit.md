---
title: "&#39;Typname&#39; kann nicht als Attribut verwendet werden, da es als &#39;MustInherit&#39; deklariert ist. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31506"
  - "bc31506"
helpviewer_keywords: 
  - "BC31506"
ms.assetid: ea2baf3d-b8e8-4738-9b6d-53409fc4d282
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Typname&#39; kann nicht als Attribut verwendet werden, da es als &#39;MustInherit&#39; deklariert ist.
Benutzerdefinierte Attributklassen können nicht als `MustInherit` deklariert werden.  
  
 **Fehler\-ID:** BC31506  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den `MustInherit`\-Modifizierer aus benutzerdefinierten Attributen.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)