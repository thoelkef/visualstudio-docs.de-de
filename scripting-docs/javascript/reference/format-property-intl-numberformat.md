---
title: "format-Eigenschaft (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format-Eigenschaft (Intl.NumberFormat)
Gibt eine Funktion zurück, die mithilfe der angegebenen Zahlenformatierungseinstellungen eine gebietsschemaspezifische Zahl formatiert.  
  
## Syntax  
  
```  
numberFormatObj.format  
```  
  
#### Parameter  
 `numberFormatObj`  
 Erforderlich.  Der Name des `NumberFormat`\-Objekts, das als Formatierung verwendet wird.  
  
## Hinweise  
 Die durch die `format`\-Eigenschaft zurückgegebene Funktion akzeptiert ein einzelnes Argument, `value`, und gibt mithilfe der im `NumberFormat`\-Objekt angegeben Optionen eine Zeichenfolge zurück, die die lokalisierte Zahl darstellt.  Wenn `value` nicht bereitgestellt wird, gibt die Funktion `NaN` \(keine Zahl\) zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird ein `NumberFormat`\-Objekt zum Erstellen einer lokalisierten Zahl verwendet.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]  
  
## Siehe auch  
 [Intl.NumberFormat\-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)