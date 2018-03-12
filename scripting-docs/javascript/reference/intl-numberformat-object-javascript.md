---
title: Intl.NumberFormat-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat-Objekt (JavaScript)
Stellt gebietsschemaspezifische Zahlenformatierung bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parameter  
 `numberFormatObj`  
 Erforderlich. Der Variablenname, der dem `NumberFormat`-Objekt zugewiesen wird.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Zahlenformatierungsoptionen. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
## <a name="remarks"></a>Hinweise  
 Die `locales` Parameter entsprechen [BCP-47](http://tools.ietf.org/html/rfc5646) Sprach- oder gebietsschematags Tags wie "En-US" und "Zh-CN". Das Tag enthält möglicherweise Sprache, Region, Land und Varianten. Beispiele für Sprachtags, finden Sie unter [Anhang A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Für `NumberFormat`, fügen Sie möglicherweise die **-u** gebietsschemazeichenfolge gefolgt - Nu, um eine zahlensystemerweiterung anzugeben:  
  
 "*Sprache*-*Region*-u-Nu -*Numberingsystem*"  
  
 wobei *Numberingsystem* einer der folgenden sein: arabische, Arabext, schmuggelte., Beng, Delta, Fullwide, Gujr, Experte, Hanidec, Khmr, Knda, Laoo, Latn, Wagen, Mylm, Mong, Mymr, Orya, Tamldec, Telu, Thai, Tibt.  
  
 Der `options`-Parameter enthält möglicherweise die folgenden Eigenschaften:  
  
|Eigenschaft|Beschreibung|Mögliche Werte|Standardwert|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Gibt den zu verwendenden Algorithmus für die Gebietsschemaübereinstimmung an.|"lookup", "best fit"|"best fit"|  
|`style`|Legt das Zahlenformat fest.|"decimal", "percent", "currency"|"decimal"|  
|`currency`|Legt den ISO 4217-Währungswert in Form von alphabetischem Code fest. Wird `style` auf "currency" festgelegt, ist dieser Wert erforderlich.|Finden Sie unter den ISO [Währung "und" Betrag code Liste](http://www.currency-iso.org/en/home/tables/table-a1.html).|nicht definiert|  
|`currencyDisplay`|Gibt an, ob die Währung als alphabetischer ISO 4217-Code, ein lokalisiertes Währungssymbol oder lokalisierter Währungsname angezeigt wird. Dieser Wert wird nur verwendet, wenn `style` auf "currency" gesetzt wird.|"code", "symbol", "name"|"symbol"|  
|`useGrouping`|Gibt an, ob ein Gruppierungstrennzeichen verwendet werden soll.|true, false|`true`.|  
|`minimumIntegerDigits`|Gibt die minimale Anzahl von zu verwendenden ganzzahligen Ziffern an.|1 bis 21.|21|  
|`minimumFractionDigits`|. Gibt die minimale Anzahl von zu verwendenden Dezimalstellen an.|0 bis 20.|0|  
|`maximumFractionDigits`|Gibt die maximale Anzahl von zu verwendenden Dezimalstellen an.|Dieser Wert kann zwischen `minimumFractionDigits` und 20 liegen.|20.|  
|`minimumSignificantDigits`|Gibt die minimale Anzahl von anzuzeigenden Dezimalstellen an.|Dieser Wert kann zwischen 1 und 21 liegen.|1|  
|`maximumSignificantDigits`|Gibt die maximale Anzahl von anzuzeigenden Dezimalstellen an.|Dieser Wert kann zwischen `minimumSignificantDigits` auf 21.|21|  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `NumberFormat`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-numberformat.md)|Gibt die Funktion an, durch die ein Zahlenformatierungs-Objekt erstellt wird.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Gibt eine Funktion zurück, die eine Zahl unter Verwendung der Zahlenformatierungseinstellungen formatiert.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-numberformat.md)|Gibt einen Verweis auf den Prototyp einer Zahlenformatierungsfunktion zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `NumberFormat`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Gibt ein Objekt zurück, das die Eigenschaften und die Werte des Zahlenformatierungsobjekts enthält.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `NumberFormat`-Objekt für das "en-US"-Gebietsschema mit den angegebenen Formatierungsoptionen erstellt.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele veranschaulichen das Ergebnis der Anwendung mehrerer unterschiedlicher Gebietsschemas und Optionen.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToLocaleString (Anzahl)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)