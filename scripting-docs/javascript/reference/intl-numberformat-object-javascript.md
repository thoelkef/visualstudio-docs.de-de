---
title: "Intl.NumberFormat-Objekt (JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat-Objekt (JavaScript)
Stellt gebietsschemaspezifische Zahlenformatierung bereit.  
  
## Syntax  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### Parameter  
 `numberFormatObj`  
 Erforderlich.  Der Variablenname, der dem `NumberFormat`\-Objekt zugewiesen wird.  
  
 `locales`  
 Optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
 `options`  
 Optional.  Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Zahlenformatierungsoptionen.  Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
## Hinweise  
 Der `locales`\-Parameter muss den [BCP 47](http://tools.ietf.org/html/rfc5646)\-Sprach\- oder Gebietsschematags entsprechen, beispielsweise "en\-US" und "zh\-CN".  Das Tag enthält möglicherweise Sprache, Region, Land und Varianten.  Beispiele für Sprachtags finden Sie unter [Anhang A](http://tools.ietf.org/html/rfc5646#appendix-A) von BCP 47.  Für `NumberFormat` fügen Sie möglicherweise das untergeordnete Tag **\-u** gefolgt von "\-nu" hinzu, um eine Zahlensystemerweiterung anzugeben:  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 wobei *numberingsystem* möglicherweise eines der folgenden ist: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt.  
  
 Der `options`\-Parameter enthält möglicherweise die folgenden Eigenschaften:  
  
|Eigenschaft|Beschreibung|Mögliche Werte|Standardwert|  
|-----------------|------------------|--------------------|------------------|  
|`localeMatcher`|Gibt den zu verwendenden Algorithmus für die Gebietsschemaübereinstimmung an.|"lookup", "best fit"|"best fit"|  
|`style`|Legt das Zahlenformat fest.|"decimal", "percent", "currency"|"decimal"|  
|`currency`|Legt den ISO 4217\-Währungswert in Form von alphabetischem Code fest.  Wird `style` auf "currency" festgelegt, ist dieser Wert erforderlich.|Weitere Informationen finden Sie in der ISO\-Liste [Current currency & funds code](http://www.currency-iso.org/en/home/tables/table-a1.html).|nicht definiert|  
|`currencyDisplay`|Gibt an, ob die Währung als alphabetischer ISO 4217\-Code, ein lokalisiertes Währungssymbol oder lokalisierter Währungsname angezeigt wird.  Dieser Wert wird nur verwendet, wenn `style` auf "currency" gesetzt wird.|"code", "symbol", "name"|"symbol"|  
|`useGrouping`|Gibt an, ob ein Gruppierungstrennzeichen verwendet werden soll.|true, false|`true`.|  
|`minimumIntegerDigits`|Gibt die minimale Anzahl von zu verwendenden ganzzahligen Ziffern an.|1 bis 21.|21|  
|`minimumFractionDigits`|.  Gibt die minimale Anzahl von zu verwendenden Dezimalstellen an.|0 bis 20.|0|  
|`maximumFractionDigits`|Gibt die maximale Anzahl von zu verwendenden Dezimalstellen an.|Dieser Wert kann zwischen `minimumFractionDigits` und 20 liegen.|20.|  
|`minimumSignificantDigits`|Gibt die minimale Anzahl von anzuzeigenden Dezimalstellen an.|Dieser Wert kann zwischen 1 und 21 liegen.|1|  
|`maximumSignificantDigits`|Gibt die maximale Anzahl von anzuzeigenden Dezimalstellen an.|Dieser Wert kann zwischen `minimumSignificantDigits` und 21 liegen.|21|  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `NumberFormat`\-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[constructor](../../javascript/reference/constructor-property-intl-numberformat.md)|Gibt die Funktion an, durch die ein Zahlenformatierungs\-Objekt erstellt wird.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Gibt eine Funktion zurück, die eine Zahl unter Verwendung der Zahlenformatierungseinstellungen formatiert.|  
|[prototype](../../javascript/reference/prototype-property-intl-numberformat.md)|Gibt einen Verweis auf den Prototyp einer Zahlenformatierungsfunktion zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `NumberFormat`\-Objekts aufgelistet.  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Gibt ein Objekt zurück, das die Eigenschaften und die Werte des Zahlenformatierungsobjekts enthält.|  
  
## Beispiel  
 Im folgenden Beispiel wird ein `NumberFormat`\-Objekt für das "en\-US"\-Gebietsschema mit den angegebenen Formatierungsoptionen erstellt.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## Beispiel  
 Die folgenden Beispiele veranschaulichen das Ergebnis der Anwendung mehrerer unterschiedlicher Gebietsschemas und Optionen.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator\-Objekt](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat\-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)