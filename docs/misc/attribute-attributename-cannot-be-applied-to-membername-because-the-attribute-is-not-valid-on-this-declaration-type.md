---
title: "Das Attribut &#39;&lt;attributname&gt;&#39; kann nicht auf &#39;&lt;membername&gt;&#39; angewendet werden, da das Attribut f&#252;r diesen Deklarationstyp nicht g&#252;ltig ist | Microsoft Docs"
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
  - "vbc30662"
  - "bc30662"
helpviewer_keywords: 
  - "BC30662"
ms.assetid: 5cd07950-37d0-45e9-8770-3eaac54ff7d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Attribut &#39;&lt;attributname&gt;&#39; kann nicht auf &#39;&lt;membername&gt;&#39; angewendet werden, da das Attribut f&#252;r diesen Deklarationstyp nicht g&#252;ltig ist
Das verwendete Attribut ist für das verwendete Element nicht geeignet.  
  
 **Fehler\-ID:** BC30662  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie ein Attribut aus, das für das verwendete Element vorgesehen ist. Wenn Sie beispielsweise eine Methode verwenden, wählen Sie ein Attribut aus, das für die Verwendung in Methoden bestimmt ist.  
  
2.  Wenn Sie selbst entwickelte benutzerdefinierte Attribute verwenden, ändern Sie das `AttributeUsage`\-Attribut so, dass es zur Art des verwendeten Elements passt.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)