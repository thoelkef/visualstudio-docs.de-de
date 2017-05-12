---
title: "Unerwarteter Quantifizierer (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Unerwarteter Quantifizierer (JavaScript)
Sie haben beim Verfassen des Suchmusters mit einem regulären Ausdruck ein Musterelement mit einem ungültigen Wiederholungsfaktor erstellt.  Beispielsweise ist das Muster  
  
```  
/^+/  
```  
  
 ungültig, weil das Element ^ \(Start der Eingabe\) keinen Wiederholungsfaktor enthalten darf.  Die folgende Tabelle enthält eine Liste der Elemente, die keine Wiederholungsfaktoren enthalten dürfen.  
  
|Element|Beschreibung|  
|-------------|------------------|  
|^|Anfang der Eingabe|  
|$|Ende der Eingabe|  
|\\b|Wortgrenze|  
|\\B|Nicht\-Wortgrenze|  
|\*|Null \(0\) oder mehr Wiederholungen|  
|\+|Eine oder mehr Wiederholungen|  
|?|Null \(0\) oder eine Wiederholung|  
|{n}|n\-Wiederholungen|  
|{n,}|n oder mehr Wiederholungen|  
|{n,m}|Zwischen n und m \(einschließlich\) Wiederholungen|  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass das Suchmusterelement nur gültige Wiederholungsfaktoren enthält.  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)