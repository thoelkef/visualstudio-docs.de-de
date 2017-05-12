---
title: "format-Eigenschaft (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format-Eigenschaft (Intl.DateTimeFormat)
Gibt eine Funktion zurück, die mithilfe der angegebenen Formatierungseinstellungen für Datum\/Uhrzeit ein gebietsschemaspezifisches Datum formatiert.  
  
## Syntax  
  
```  
dateTimeFormatObj.format  
```  
  
#### Parameter  
 `dateTimeFormatObj`  
 Erforderlich.  Der Name des `DateTimeFormat`\-Objekts, das als Formatierung verwendet wird.  
  
## Hinweise  
 Die durch die `format`\-Eigenschaft zurückgegebene Funktion akzeptiert ein einzelnes Argument, `date`, und gibt mithilfe der im `DateTimeFormat`\-Objekt angegeben Optionen eine Zeichenfolge zurück, die das lokalisierte Datum darstellt.  Der `date`\-Parameter der zurückgegebenen Funktion muss eine Zahl, eine Datumszeichenfolge oder ein `Date`\-Objekt sein.  Wenn `date` nicht angegeben wird, verwendet die Funktion [Date.now](../../javascript/reference/date-now-function-javascript.md) als Standardeingabewert.  
  
## Beispiel  
 Im folgenden Beispiel wird ein `DateTimeFormat`\-Objekt verwendet, um das Datum "Dec 1, 2007" für Deutsch zu lokalisieren und neu zu formatieren.  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [Intl.DateTimeFormat\-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)