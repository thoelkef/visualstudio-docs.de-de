---
title: "setTime-Methode (Datum) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime-Methode"
  - "time-Methode"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime-Methode (Datum) (JavaScript)
Legt die Werte für Datum und Uhrzeit im `Date`\-Objekt fest.  
  
## Syntax  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 *milliseconds*  
 Erforderlich.  Ein numerischer Wert für die seit Mitternacht, 1. Januar 1970 \(GMT\), vergangenen Millisekunden.  
  
## Hinweise  
 Ist *milliseconds* ein negativer Wert, verweist er auf ein Datum vor 1970.  Der Bereich verfügbarer Datumsangaben umfasst etwa 285.616 Jahre vor und nach 1970.  
  
 Das Festlegen von Datum und Uhrzeit mit der `setTime`\-Methode ist unabhängig von Zeitzonen.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setTime`\-Methode veranschaulicht.  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getTime\-Methode \(Datum\)](../../javascript/reference/gettime-method-date-javascript.md)