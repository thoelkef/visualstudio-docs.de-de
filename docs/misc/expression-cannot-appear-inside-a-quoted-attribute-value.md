---
title: "In einem Attributwert in Anf&#252;hrungszeichen d&#252;rfen keine Ausdr&#252;cke enthalten sein. | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In einem Attributwert in Anf&#252;hrungszeichen d&#252;rfen keine Ausdr&#252;cke enthalten sein.
In einem Attributwert in Anführungszeichen dürfen keine Ausdrücke enthalten sein. Entfernen Sie die Anführungszeichen.  
  
 Ein eingebetteter Ausdruck in einem Attributwert für ein XML\-Literal wird in Anführungszeichen eingeschlossen.  
  
 **Fehler\-ID:** BC31155  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die begrenzenden Anführungszeichen aus dem Attributwert. Im Folgenden finden Sie ein Beispiel dazu:  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## Siehe auch  
 [Embedded Expressions in XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)