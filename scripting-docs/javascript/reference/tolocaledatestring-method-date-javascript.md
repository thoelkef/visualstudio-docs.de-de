---
title: "toLocaleDateString-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString-Methode"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLocaleDateString-Methode (Datum) (JavaScript)
Gibt ein Datum als Zeichenfolge zurück, das dem aktuellen Gebietsschema der Hostumgebung oder dem festgelegten Gebietsschema entspricht.  
  
## Syntax  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### Parameter  
 `dateObj`  
 Erforderlich.  Ein `Date`\-Objekt.  
  
 `locales`  
 Optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  
  
 `options`  
 Optional.  Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleDateString` zum Formatieren des Datums intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird.  Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt.  Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleDateString` im Internet Explorer 10\-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Es wird ein Zeichenfolgenwert mit einem Datum in der aktuellen Zeitzone zurückgegeben.  
  
-   Das zurückgegebene Datum hat das Standardformat des aktuellen Gebietsschemas der Hostumgebung.  
  
 Wenn Sie den `locales`\-Parameter weglassen, kann bei der Skripterstellung auf den Rückgabewert dieser Methode nicht vertraut werden, da er sich von Computer zu Computer unterscheidet.  Verwenden Sie die Methode in diesem Szenario nur zum Formatieren von angezeigtem Text und niemals als Teil einer Berechnung.  
  
## Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleDateString`\-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`\- und `options`\-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [toDateString\-Methode \(Datum\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString\-Methode \(Datum\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)