---
title: Intl.Collator-Objekt (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640000"
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator-Objekt (JavaScript)
Stellt gebietsschemaspezifische Zeichenfolgenvergleiche bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Parameter  
 `collatorObj`  
 Erforderlich. Der Variablenname, der dem `Collator`-Objekt zugewiesen wird.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen. Weitere Informationen finden Sie im Abschnitt Hinweise.  
  
## <a name="remarks"></a>Hinweise  
 Die `locales` Parameter entsprechen [BCP-47](http://tools.ietf.org/html/rfc5646) Sprach- oder gebietsschematags Tags wie "En-US" und "Hans-Zh-CN". Das Tag enthält möglicherweise Sprache, Region, Land und Varianten. Eine Liste der Sprachen finden Sie unter der [IANA Sprache gebietsschemazeichenfolge Registrierung](http://go.microsoft.com/fwlink/p/?linkid=227303). Beispiele für Sprachtags, finden Sie unter [Anhang A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP-47. Für `Collator` können Sie die "-u"-Erweiterung in der Gebietsschemazeichenfolge einschließen, um einen oder mehrere der folgenden Unicode-Erweiterungen anzugeben:  
  
-   co - Variante Sortierungen (Gebietsschema) angeben: "*Sprache*-*Region*-u-co -*Wert*".  
  
-   -kn auf einen numerischen Vergleich anzugeben: "*Sprache*-*Region*- u-kn-" true "&#124;" false "".  
  
-   -Kf, um anzugeben, ob Groß-oder Kleinbuchstaben zuerst sortieren: "*Sprache*-*Region*-u Kf oben &#124; untere &#124;" false ""). Diese Erweiterung wird derzeit nicht unterstützt.  
  
 Um einen numerischen Vergleich anzugeben, können Sie die -kn-Erweiterung in der gebietsschemazeichenfolge festlegen oder verwenden Sie die `numeric` Eigenschaft in der `options` Parameter. Bei Verwendung der `numeric` -Eigenschaft der -kn Wert wird nicht angewendet.  
  
 Der `options`-Parameter enthält möglicherweise die folgenden Eigenschaften:  
  
-   `localeMatcher`. Gibt den zu verwendenden Algorithmus für die Gebietsschemaübereinstimmung an. Die möglichen Werte sind "lookup" und "best fit". Der Standardwert ist "best fit".  
  
-   `usage`. Gibt an, ob das Ziel des Vergleichs Sortierung oder Suche ist. Die möglichen Werte sind "sort" und "search". Der Standardwert ist "sort".  
  
-   `sensitivity`. Gibt die Empfindlichkeit des Sortierers an. Mögliche Werte sind "Basis", "Akzent", "Fall" und "Variante". Der Standardwert ist `undefined`.  
  
-   `ignorePunctuation`. Gibt an, ob Satzzeichen im Vergleich ignoriert werden. Die möglichen Werte sind "true" oder "false". Der Standardwert ist `false`.  
  
-   `numeric`. Gibt an, ob numerische Sortierung verwendet wird. Die möglichen Werte sind "true" oder "false". Der Standardwert ist `false`.  
  
-   `caseFirst`. Wird derzeit nicht unterstützt.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Collator`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Gibt eine Funktion, die zwei Zeichenfolgen vergleicht, mit der Sortierreihenfolge des collators verwendet.|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-collator.md)|Gibt die Funktion an, durch die ein Sortierer erstellt wird.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-collator.md)|Gibt einen Verweis auf den Prototyp für einen Sortierer zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Collator`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Gibt ein Objekt zurück, das die Eigenschaften und die Werte des Sortierers enthält.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `Collator`-Objekt erstellt und ein Vergleich ausgeführt.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden `Collator`-Objekte verwendet, um ein Array zu sortieren. Dieses Beispiel veranschaulicht gebietsschemaspezifische Unterschiede.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `Collator`-Objekt zur Suche für eine Zeichenfolge verwendet und werden Vergleichsoptionen angegeben.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [LocaleCompare-Methode (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)