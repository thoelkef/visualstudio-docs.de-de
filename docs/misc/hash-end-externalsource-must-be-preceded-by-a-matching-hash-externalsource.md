---
title: "&#39;#End ExternalSource&#39; muss ein entsprechendes &#39;#ExternalSource&#39; voranstehen. | Microsoft Docs"
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
  - "bc30578"
  - "vbc30578"
helpviewer_keywords: 
  - "BC30578"
ms.assetid: f011673d-eced-46a7-a08e-d54d86c8a76b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End ExternalSource&#39; muss ein entsprechendes &#39;#ExternalSource&#39; voranstehen.
Die `#ExternalSource`\-Anweisung verweist auf äußeren Code, sodass der Compiler genau melden kann, wenn Ausnahmen innerhalb dieses Codes auftreten. Ein `#ExternalSource`\-Block muss mit `#ExternalSource` beginnen und mit `#End ExternalSource` enden.  
  
 **Fehler\-ID:** BC30578  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie `#ExternalSource` an der gewünschten Stelle im Code hinzu.  
  
2.  Entfernen Sie `#End ExternalSource`, wenn es nicht erforderlich ist.  
  
## Siehe auch  
 [\#ExternalSource Directive](/dotnet/visual-basic/language-reference/directives/externalsource-directive)   
 [NOTINBUILD: Bedingte Kompilierung \(Visual Basic\)](http://msdn.microsoft.com/de-de/ad1e35e0-935e-4a35-a2ae-738bcf2a9240)