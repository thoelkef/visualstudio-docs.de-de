---
title: "Das Umwandeln von &quot;Date&quot; in &quot;Double&quot; erfordert das Aufrufen der Date.ToOADate-Methode. | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Umwandeln von &quot;Date&quot; in &quot;Double&quot; erfordert das Aufrufen der Date.ToOADate-Methode.
Sie haben versucht, einen `Date`\-Wert in einen `Double`\-Wert umzuwandeln, was nicht ohne die <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>\-Methode erfolgen kann.  
  
 **Fehler\-ID:** BC30532  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie die <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>\-Methode, um den Wert zu konvertieren.  
  
## Siehe auch  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)