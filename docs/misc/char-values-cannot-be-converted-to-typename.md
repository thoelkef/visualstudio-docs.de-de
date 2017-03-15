---
title: "&#39;Char&#39;-Werte k&#246;nnen nicht in &#39;&lt;Typname&gt;&#39; konvertiert werden. | Microsoft Docs"
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
  - "bc32006"
  - "vbc32006"
helpviewer_keywords: 
  - "BC32006"
ms.assetid: c033f65e-a315-47fc-be2e-ed371847a221
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Char&#39;-Werte k&#246;nnen nicht in &#39;&lt;Typname&gt;&#39; konvertiert werden.
'Char'\-Werte können nicht in '\<Typname\>' konvertiert werden. Verwenden Sie „Microsoft.VisualBasic.AscW“, um ein Zeichen als Unicode\-Wert zu interpretieren, oder „Microsoft.VisualBasic.Val“, um es als Ziffer zu interpretieren.  
  
 Ein Ausdruck versucht, einen `Char`\-Wert in einen anderen Datentyp als `String` oder `Object` zu konvertieren.  
  
 **Fehler\-ID:** BC32006  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie die `AscW`\-Funktion, um einen `Char`\-Wert als Unicode\-Zeichencode zu interpretieren, oder verwenden Sie die `Val`\-Funktion, um ihn als numerische Ziffer zu interpretieren.  
  
## Siehe auch  
 [NICHT IM BUILD: Asc\-, AscW\-Funktionen](http://msdn.microsoft.com/de-de/6814bfec-12ba-41fb-b10e-bec99750d5e1)   
 [NICHT IM BUILD: Val\-Funktion](http://msdn.microsoft.com/de-de/81650f77-9242-4ec1-8e04-e93b5daa451d)   
 [Char Data Type](/dotnet/visual-basic/language-reference/data-types/char-data-type)