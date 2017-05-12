---
title: "Der zu decodierende URI enth&#228;lt ein ung&#252;ltiges Zeichen | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Der zu decodierende URI enth&#228;lt ein ung&#252;ltiges Zeichen
Sie haben versucht, eine Zeichenfolge als URI \(Uniform Resource Identifier\) zu codieren, sie enthält jedoch ungültige Zeichen.  Die meisten Zeichen sind zwar in Zeichenfolgen, die in URI konvertiert werden sollen, zulässig, jedoch sind einige Unicode\-Zeichensequenzen ungültig.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die zu codierende Zeichenfolge nur gültige Unicode\-Sequenzen enthält.  Ein vollständiger URI ist aus einer Folge von Komponenten und Trennzeichen zusammengesetzt.  Die Namen in spitzen Klammern stellen Komponenten dar, und die Zeichen ":", "\/", ";" und "?" sind für die Verwendung als Trennzeichen reserviert.  Das allgemeine Format ist:  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## Siehe auch  
 [encodeURI\-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent\-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)