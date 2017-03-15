---
title: "System.Runtime.InteropServices.DllImportAttribute kann nicht auf &quot;Declare&quot; angewendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute kann nicht auf &quot;Declare&quot; angewendet werden.
Das `DllImportAttribute`\-Attribut wurde auf eine `Declare`\-Funktion angewendet. Dieses Attribut kann nur verwendet werden, wenn `Function` oder `Sub` leer ist.  
  
 **Fehler\-ID:** BC31523  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das `DllImportAttribute`\-Attribut aus der `Declare`\-Anweisung.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)