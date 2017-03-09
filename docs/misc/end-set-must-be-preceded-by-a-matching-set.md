---
title: "&quot;End Set&quot; muss ein entsprechendes &quot;Set&quot; voranstehen | Microsoft Docs"
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
  - "bc30632"
  - "vbc30632"
helpviewer_keywords: 
  - "BC30632"
ms.assetid: 0c3dd065-566b-485c-9996-6177eb0fde39
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Set&quot; muss ein entsprechendes &quot;Set&quot; voranstehen
`End Set` dient zum Beenden von `Set`\-Eigenschaftenprozeduren. Das `End Set`\-Konstrukt wurde außerhalb einer `Set`\-Eigenschaftenprozedur gefunden.  
  
 **Fehler\-ID:** BC30632  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass die `Set`\-Eigenschaftenprozedur nach einem `Property`\-Schlüsselwort und vor dem `End Property`\-Konstrukt deklariert wird.  
  
2.  Stellen Sie sicher, dass die `Set`\-Eigenschaftenprozedur mit dem `Set`\-Schlüsselwort beginnt und mit einem `End Set`\-Konstrukt endet.  
  
## Siehe auch  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/de-de/1c138efa-9bc2-44d7-80a0-f3a7c2510264)