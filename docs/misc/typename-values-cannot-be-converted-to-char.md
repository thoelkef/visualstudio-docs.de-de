---
title: "&#39;&lt;typname&gt;&#39;-Werte k&#246;nnen nicht in &#39;Char&#39; konvertiert werden | Microsoft Docs"
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
  - "bc32007"
  - "vbc32007"
helpviewer_keywords: 
  - "BC32007"
ms.assetid: b04212da-57ac-4493-9480-04c12b50f875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typname&gt;&#39;-Werte k&#246;nnen nicht in &#39;Char&#39; konvertiert werden
'\<typname\>'\-Werte können nicht in 'Char' konvertiert werden. Verwenden Sie Microsoft.VisualBasic.ChrW, um einen numerischen Wert als Unicode\-Zeichen zu interpretieren, oder konvertieren Sie ihn zuerst in 'String', um eine Ziffer zu erzeugen.  
  
 Ein Ausdruck versucht, einen anderen Datentyp als `String` oder `Object` in `Char` zu konvertieren.  
  
 **Fehler\-ID:** BC32007  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie die `ChrW`\-Funktion, um einen numerischen Wert in ein Unicode\-Zeichen oder den Wert zuerst in `String` und dann in `Char` zu konvertieren.  
  
## Siehe auch  
 [NICHT IM BUILD: Funktionen 'Chr', 'ChrW'](http://msdn.microsoft.com/de-de/37f3c707-8a6f-4c51-9b02-9e634c4299ab)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Char Data Type](/dotnet/visual-basic/language-reference/data-types/char-data-type)