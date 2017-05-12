---
title: "toLocaleTimeString-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString-Methode"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toLocaleTimeString-Methode (Datum) (JavaScript)
Gibt eine Zeit als Zeichenfolge zurück, das dem aktuellen Gebietsschema der Hostumgebung oder dem festgelegten Gebietsschema entspricht.  
  
## Syntax  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### Parameter  
 `dateObj`  
 Erforderlich.  Ein `Date`\-Objekt.  
  
 `locales`  
 Dies ist optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  
  
 `options`  
 Dies ist optional.  Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleTimeString` zum Formatieren der Zeit intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird.  Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt.  Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleTimeString` im Internet Explorer 10\-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Es wird ein Zeichenfolgenwert mit einer Zeit in der aktuellen Zeitzone zurückgegeben.  
  
-   Die zurückgegebene Zeit hat das Standardformat des aktuellen Gebietsschemas der Hostumgebung.  
  
 Wenn Sie den `locales`\-Parameter weglassen, kann bei der Skripterstellung auf den Rückgabewert dieser Methode nicht vertraut werden, da er sich von Computer zu Computer unterscheidet.  Verwenden Sie die Methode in diesem Szenario nur zum Formatieren von angezeigtem Text und niemals als Teil einer Berechnung.  
  
## Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleTimeString`\-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`\- und `options`\-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [toTimeString\-Methode \(Datum\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString\-Methode \(Datum\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)