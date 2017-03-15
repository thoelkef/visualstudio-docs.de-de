---
title: "Der Typ &#39;&lt;Typname&gt;&#39; muss ein Werttyp oder ein Typargument sein, das auf &#39;Structure&#39; eingeschr&#228;nkt ist, damit er mit &#39;Nullable&#39; oder dem Modifizierer &#39;?&#39;, der NULL-Werte zul&#228;sst, verwendet werden kann. | Microsoft Docs"
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
  - "vbc33101"
  - "bc33101"
helpviewer_keywords: 
  - "BC33101"
ms.assetid: b3e0e4e4-87b8-4a38-a450-15233497acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &#39;&lt;Typname&gt;&#39; muss ein Werttyp oder ein Typargument sein, das auf &#39;Structure&#39; eingeschr&#228;nkt ist, damit er mit &#39;Nullable&#39; oder dem Modifizierer &#39;?&#39;, der NULL-Werte zul&#228;sst, verwendet werden kann.
Nur Werttypen, einschließlich Strukturen, können als 'Nullable' deklariert werden.  
  
```vb#  
' Valid. Dim n? As Integer Dim m As Integer? ' Not valid. ' Dim p? As Object ' Dim q As Nullable(Of Object)  
```  
  
 **Fehler\-ID:** BC33101  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das '?' oder `Nullable`.  
  
-   Verwenden Sie einen Wertdatentyp.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)