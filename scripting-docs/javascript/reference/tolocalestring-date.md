---
title: "toLocaleString (Date) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
Konvertiert ein Datum mithilfe des aktuellen oder angegebenen Gebietsschemas in eine Zeichenfolge.  
  
## Syntax  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### Parameter  
 `dateObj`  
 Erforderlich.  Das zu konvertierende `Date`\-Objekt.  
  
 `locales`  
 Optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  
  
 `options`  
 Optional.  Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleString` zum Vergleichen intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird.  Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt.  Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleString` im Internet Explorer 10\-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Gibt ein `String`\-Objekt zurück, in dem das Datum im langen Standardformat des aktuellen Gebietsschemas enthalten ist.  
  
-   Für Tage zwischen 1601 und 1999 wird das Datum entsprechend den Ländereinstellungen formatiert, die in der Systemsteuerung des Benutzers definiert sind.  
  
> [!NOTE]
>  Wenn Sie den `locales`\-Parameter weglassen, verwenden Sie `toLocaleString` nur, um die Ergebnisse einem Benutzer anzuzeigen. Verwenden Sie ihn niemals, um Werte innerhalb eines Skripts zu berechnen, da das zurückgegebene Ergebnis computerspezifisch ist.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toLocaleString`\-Methode gezeigt.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleString`\-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales`\- und `options`\-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [toLocaleDateString\-Methode \(Datum\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)