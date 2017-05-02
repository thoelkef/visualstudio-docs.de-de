---
title: "normalize-Methode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# normalize-Methode (String) (JavaScript)
Gibt die Unicode\-Normalisierungsform einer angegebenen Zeichenfolge zurück.  
  
## Syntax  
  
```  
stringObj.normalize([form]);  
```  
  
#### Parameter  
 `stringObj`  
 Erforderlich.  Das string\-Objekt für den Test.  
  
 `form`  
 Dies ist optional.  Der Unicode\-Normalisierungsformwert.  
  
## Rückgabewert  
 Die Unicode\-Normalisierungsform einer angegebenen Zeichenfolge.  
  
## Ausnahmen  
 Wenn `form` kein unterstützter Wert ist, wird ein `RangeError` ausgelöst.  
  
## Hinweise  
 Wenn `stringObj` keine Zeichenfolge ist, erfolgt eine Konvertierung in eine Zeichenfolge, bevor die Methode versucht, die Unicode\-Normalisierungsform der Zeichenfolge zurückzugeben.  
  
 `form` muss ein Unicode\-Normalisierungsformwert \("NFC", "NFD", "NFKC" oder "NFKD"\) entsprechend den Werten sein, die für [Unicode Standard Annex \#15](http://www.unicode.org/reports/tr15/) angegeben sind.  Der Standardwert von `form` ist "NFC".  
  
## Beispiel  
 Die folgenden Codebeispiele veranschaulichen die Verwendung der `normalize`Methode.  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]