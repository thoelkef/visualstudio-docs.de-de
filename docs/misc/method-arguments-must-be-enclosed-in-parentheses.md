---
title: "Methodenargumente m&#252;ssen in Klammern stehen. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30800"
  - "bc30800"
helpviewer_keywords: 
  - "BC30800"
ms.assetid: ecdec760-8b51-474f-acad-17cf8059d83b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methodenargumente m&#252;ssen in Klammern stehen.
Die Regeln, die Prozeduraufrufe steuern, sind in neueren Versionen von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] einfacher. Alle Argumente müssen in Klammern stehen.  
  
 **Fehler\-ID:** BC30800  
  
### So beheben Sie diesen Fehler  
  
-   Schließen Sie die Argumentliste in Klammern ein. Beispiel:  
  
    ```  
    MySub(ArrayIndex, NewValue)  
    ```  
  
## Siehe auch  
 [Procedure Calling Sequence Changes in Visual Basic](http://msdn.microsoft.com/de-de/4ef1eea6-36cb-4b97-a31b-9ba65e46a9fd)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)