---
title: "Der zu decodierende URI ist keine g&#252;ltige Codierung | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Der zu decodierende URI ist keine g&#252;ltige Codierung
Sie haben versucht, einen falsch formatierten URI \(Uniform Resource Identifier\) zu decodieren.  URIs weisen eine besondere Syntax auf. Die meisten nicht alphanumerischen Zeichen müssen vor der Verwendung in einem URI codiert werden.  Sie können die Methoden `encodeURI` und `encodeURIComponent` verwenden, um einen URI aus einer normalen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Zeichenfolge zu erstellen.  
  
 Ein vollständiger URI ist aus einer Folge von Komponenten und Trennzeichen zusammengesetzt.  Das allgemeine Format ist:  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Die Namen in spitzen Klammern stellen Komponenten dar, und die Zeichen ":", "\/", ";" und "?" sind für die Verwendung als Trennzeichen reserviert.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass nur gültige URIs decodiert werden.  Normale [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Zeichenfolgen können nicht decodiert werden, da sie möglicherweise ungültige Zeichen enthalten.  
  
## Siehe auch  
 [decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)