---
title: "Typzeichen k&#246;nnen nicht in einer Sub-Deklaration verwendet werden, da eine &#39;Sub&#39; keinen Wert zur&#252;ckgibt. | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typzeichen k&#246;nnen nicht in einer Sub-Deklaration verwendet werden, da eine &#39;Sub&#39; keinen Wert zur&#252;ckgibt.
Eine `Sub`\-Prozedur wie die `Function`\-Prozedur ist eine separate Prozedur, die Argumente annehmen und eine Reihe von Anweisungen ausführen kann. Im Gegensatz zu einer `Function`\-Prozedur, gibt eine `Sub` keinen Wert zurück und kann daher keine Typdeklaration enthalten.  
  
 **Fehler\-ID:** BC30303  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die `Sub`\-Prozedur in eine `Function`\-Prozedur.  
  
## Siehe auch  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)