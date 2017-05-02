---
title: "Im regul&#228;ren Ausdruck wurde &#39;)&#39; erwartet (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Im regul&#228;ren Ausdruck wurde &#39;)&#39; erwartet (JavaScript)
Sie haben versucht, eine Aufzeichnung, eine Assertion oder eine Gruppe für reguläre Ausdrücke zu erstellen, haben jedoch nicht die schließende Klammer einbezogen.  Klammern haben mehrere Zwecke in regulären Ausdrücken.  Hauptsächlich werden sie verwendet, um Teilausdrücke aufzuzeichnen, Assertionen anzugeben oder Muster zu gruppieren, sodass die Elemente als einzelne Einheit von \*, \+? usw. behandelt werden können.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie die am weitesten rechts befindlichen schließenden Klammer hinzu.  
  
    > [!NOTE]
    >  Wenn Sie eine einzelne Klammer anpassen möchten, versehen Sie diese mit einem umgekehrten Schrägstrich \- \\\( \- als Escapezeichen, damit es nicht als Sonderzeichen von [!INCLUDE[javascript](../../includes/javascript-md.md)] interpretiert wird.  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)