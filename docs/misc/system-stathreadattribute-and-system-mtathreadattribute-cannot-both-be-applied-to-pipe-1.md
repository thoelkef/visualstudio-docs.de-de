---
title: "System.STAThreadAttribute und System.MTAThreadAttribute k&#246;nnen nicht zusammen auf &quot;|1&quot; angewendet werden. | Microsoft Docs"
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
  - "bc31513"
  - "vbc31513"
helpviewer_keywords: 
  - "BC31513"
ms.assetid: 7efb4c8e-d31c-4273-9d85-8cd2bef4d120
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.STAThreadAttribute und System.MTAThreadAttribute k&#246;nnen nicht zusammen auf &quot;|1&quot; angewendet werden.
Die Attribute `System.STAThreadAttribute` und `System.MTAThreadAttribute` schließen sich gegenseitig aus.  
  
 **Fehler\-ID:** BC31513  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie entweder `System.MTAThreadAttribute` oder `System.STAThreadAttribute` an, aber nicht beide Attribute zusammen.  
  
## Siehe auch  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)