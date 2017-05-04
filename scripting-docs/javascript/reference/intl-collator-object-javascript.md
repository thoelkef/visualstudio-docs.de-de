---
title: "Intl.Collator-Objekt (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.Collator-Objekt (JavaScript)
Stellt gebietsschemaspezifische Zeichenfolgenvergleiche bereit.  
  
## Syntax  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### Parameter  
 `collatorObj`  
 Erforderlich.  Der Variablenname, der dem `Collator`\-Objekt zugewiesen wird.  
  
 `locales`  
 Optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
 `options`  
 Optional.  Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
## Hinweise  
 Der `locales`\-Parameter muss den [BCP 47](http://tools.ietf.org/html/rfc5646)\-Sprach\- oder Gebietsschematags wie "en\-US" und "Zh\-HansCN" entsprechen.  Das Tag enthält möglicherweise Sprache, Region, Land und Varianten.  Eine Liste der Sprachen finden Sie in der [Registrierung untergeordneter IANA\-Sprachtags](http://go.microsoft.com/fwlink/p/?linkid=227303).  Beispiele für Sprachtags finden Sie unter [Anhang A](http://tools.ietf.org/html/rfc5646#appendix-A) von BCP 47.  Für `Collator` können Sie die "\-u"\-Erweiterung in der Gebietsschemazeichenfolge einschließen, um einen oder mehrere der folgenden Unicode\-Erweiterungen anzugeben:  
  
-   \-co, um variante Sortierreihenfolgen anzugeben \(gebietsschemaspezifisch\): "*language*\-*region*\-u\-co\-*value*".  
  
-   \-kn, um einen numerischen Vergleich anzugeben: "*language*\-*region*\-u\-kn\-true&#124;false".  
  
-   \-kf, um anzugeben, ob Groß\- oder Kleinbuchstaben zuerst sortiert werden: "*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\).  Diese Erweiterung wird derzeit nicht unterstützt.  
  
 Um einen numerischen Vergleich anzugeben, können Sie die "–kn"\-Erweiterung in der Gebietsschemazeichenfolge festlegen oder die `numeric`\-Eigenschaft im `options`\-Parameter verwenden.  Wenn Sie die `numeric`\-Eigenschaft verwenden, trifft der \-kn Wert nicht zu.  
  
 Der `options`\-Parameter enthält möglicherweise die folgenden Eigenschaften:  
  
-   `localeMatcher`.  Gibt den zu verwendenden Algorithmus für die Gebietsschemaübereinstimmung an.  Die möglichen Werte sind "lookup" und "best fit".  Der Standardwert ist "best fit".  
  
-   `usage`.  Gibt an, ob das Ziel des Vergleichs Sortierung oder Suche ist.  Die möglichen Werte sind "sort" und "search".  Der Standardwert ist "sort".  
  
-   `sensitivity`.  Gibt die Empfindlichkeit des Sortierers an.  Mögliche Werte sind "Basis", "Akzent", "Fall" und "Variante".  Der Standardwert ist `undefined`.  
  
-   `ignorePunctuation`.  Gibt an, ob Satzzeichen im Vergleich ignoriert werden.  Die möglichen Werte sind "true" oder "false".  Der Standardwert ist `false`.  
  
-   `numeric`.  Gibt an, ob numerische Sortierung verwendet wird.  Die möglichen Werte sind "true" oder "false".  Der Standardwert ist `false`.  
  
-   `caseFirst`.  Wird derzeit nicht unterstützt.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Collator`\-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Gibt eine Funktion zurück, die zwei Zeichenfolgen vergleicht, indem die Sortierreihenfolge des Collators verwendet wird.|  
|[constructor](../../javascript/reference/constructor-property-intl-collator.md)|Gibt die Funktion an, durch die ein Sortierer erstellt wird.|  
|[prototype](../../javascript/reference/prototype-property-intl-collator.md)|Gibt einen Verweis auf den Prototyp für einen Sortierer zurück.|  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden des `Collator`\-Objekts aufgelistet.  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Gibt ein Objekt zurück, das die Eigenschaften und die Werte des Sortierers enthält.|  
  
## Beispiel  
 Im folgenden Beispiel wird ein `Collator`\-Objekt erstellt und ein Vergleich ausgeführt.  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## Beispiel  
 Im folgenden Beispiel werden `Collator`\-Objekte verwendet, um ein Array zu sortieren.  Dieses Beispiel veranschaulicht gebietsschemaspezifische Unterschiede.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird ein `Collator`\-Objekt zur Suche für eine Zeichenfolge verwendet und werden Vergleichsoptionen angegeben.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [localeCompare\-Methode \(String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat\-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat\-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)