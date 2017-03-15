---
title: "&#39;System.STAThreadAttribute&#39; und &#39;System.MTAThreadAttribute&#39; k&#246;nnen nicht zusammen auf dieselbe Methode angewendet werden. | Microsoft Docs"
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
  - "vbc31512"
  - "bc31512"
helpviewer_keywords: 
  - "BC31512"
ms.assetid: ee27e834-707d-4f02-86d4-831fa9bd2359
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.STAThreadAttribute&#39; und &#39;System.MTAThreadAttribute&#39; k&#246;nnen nicht zusammen auf dieselbe Methode angewendet werden.
Die Attribute `System.STAThreadAttribute` und `System.MTAThreadAttribute` schließen sich gegenseitig aus.  
  
 **Fehler\-ID:** BC31512  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie entweder `System.MTAThreadAttribute` oder `System.STAThreadAttribute` an, aber nicht beide Attribute zusammen.  
  
## Siehe auch  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)