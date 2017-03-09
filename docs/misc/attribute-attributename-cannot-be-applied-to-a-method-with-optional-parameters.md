---
title: "Das Attribut &lt;Attributname&gt; kann nicht auf eine Methode mit optionalen Parametern angewendet werden. | Microsoft Docs"
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
  - "vbc30645"
  - "bc30645"
helpviewer_keywords: 
  - "BC30645"
ms.assetid: 4de3d2c9-5588-47c2-a6b2-e165d16106b8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Attribut &lt;Attributname&gt; kann nicht auf eine Methode mit optionalen Parametern angewendet werden.
Das Attribut kann nur auf Methoden, die die erforderlichen Argumente oder keine Argumente verwenden, angewendet werden.  
  
 **Fehler\-ID:** BC30645  
  
### So beheben Sie diesen Fehler  
  
1.  Definieren Sie die Methode ohne optionale Parameter.  
  
2.  Verwenden Sie ein Attribut, das auf Methoden angewendet werden kann, die optionalen Parameter aufweisen.  
  
3.  Definieren Sie ein benutzerdefiniertes Attribut, das in diesem Kontext verwendet werden kann.  
  
## Siehe auch  
 <xref:System.AttributeUsageAttribute>   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)