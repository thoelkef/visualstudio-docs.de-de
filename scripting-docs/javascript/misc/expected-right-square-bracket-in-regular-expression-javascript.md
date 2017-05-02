---
title: "Im regul&#228;ren Ausdruck wurde &#39;]&#39; erwartet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Im regul&#228;ren Ausdruck wurde &#39;]&#39; erwartet (JavaScript)
Sie haben versucht, eine Zeichenklasse für die Übereinstimmung eines regulären Ausdrucks zu erstellen. Die rechte Klammer ist jedoch nicht enthalten.  Einzelne Literalzeichenkombinationen können in Zeichenklassen zusammengefasst werden, indem sie innerhalb der Klammern platziert werden.  Eine Zeichenklasse entspricht allen enthaltenen Zeichen.  So entspricht beispielsweise \/\[abc\]\/ einem der Zeichen "a", "b" oder "c".  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie die rechte Klammer dem regulären Ausdruck hinzu.  
  
    > [!NOTE]
    >  Wenn Sie eine einzelne Klammer anpassen möchten, versehen Sie diese mit einem umgekehrten Schrägstrich \- \\\[ \- als Escapezeichen, damit es nicht als Sonderzeichen von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] interpretiert wird.  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)