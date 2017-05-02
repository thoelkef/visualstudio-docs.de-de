---
title: "toUTCString-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString-Methode"
  - "UTC-Datumsangaben, Konvertieren in Zeichenfolgen"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString-Methode (Datum) (JavaScript)
Gibt ein Datum zurück, das unter Verwendung von UTC \(Universal Time Coordinated, koordinierte Weltzeit\) in eine Zeichenfolge konvertiert wurde.  
  
## Syntax  
  
```  
  
dateObj.toUTCString()   
```  
  
## Hinweise  
 Der erforderliche `dateObj`\-Verweis ist ein beliebiges `Date`\-Objekt.  
  
 Die `toUTCString`\-Methode gibt ein `String`\-Objekt zurück, das das gemäß UTC\-Konvention formatierte Datum in einem benutzerfreundlichen, leicht lesbaren Format enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toUTCString`\-Methode veranschaulicht.  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [toGMTString\-Methode \(Datum\)](../../javascript/reference/togmtstring-method-date-javascript.md)