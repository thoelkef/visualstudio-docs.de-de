---
title: "toString-Methode (Datum) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString-Methode (Datum)
Gibt eine Zeichenfolgendarstellung eines Datums zurück.  Das Format der Zeichenfolge hängt vom Gebietsschema ab.  Für U.S.\-Englisch \(en\-us\) lautet es wie folgt:  
  
 *Wochentag* *Monat* *Tag* *Stunde*: *Minute*:*Sekunde* *Zeitzone* *Jahr*  
  
## Syntax  
  
```  
  
date.toString()  
```  
  
## Parameter  
 `date`  
 Erforderlich.  Das als Zeichenfolge darzustellende Datum.  
  
## Rückgabewert  
 Gibt die Zeichenfolgendarstellung des Datums zurück.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `toString`\-Methode mit einem Datum.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]