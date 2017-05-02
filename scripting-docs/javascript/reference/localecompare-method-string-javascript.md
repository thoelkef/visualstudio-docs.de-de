---
title: "localeCompare-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare-Methode"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare-Methode (String) (JavaScript)
Bestimmt, ob zwei Zeichenfolgen im aktuellen Gebietsschema gleich sind.  
  
## Syntax  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## Parameter  
 `stringVar`  
 Erforderlich.  Die erste zu vergleichende Zeichenfolge.  
  
 `stringExp`  
 Erforderlich.  Die zweite zu vergleichende Zeichenfolge.  
  
 `locales`  
 Optional.  Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach\- oder Gebietsschematags enthält.  Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist.  Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript\-Laufzeit verwendet.  Dieser Parameter muss den [BCP 47](http://tools.ietf.org/html/rfc5646)\-Standards entsprechen. Informationen hierzu finden Sie unter [Intl.Collator\-Objekt](../../javascript/reference/intl-collator-object-javascript.md).  
  
 `options`  
 Optional.  Ein Objekt, das eine oder mehrere Eigenschaften enthält, die Vergleichsoptionen angeben. Informationen hierzu finden Sie unter [Intl.Collator\-Objekt](../../javascript/reference/intl-collator-object-javascript.md).  
  
## Hinweise  
 Für die Vergleichszeichenfolgen können Sie entweder `String`\-Objekte oder Zeichenfolgenliteralen angeben.  
  
 Ab Internet Explorer 11 verwendet `localeCompare` zum Vergleichen intern das `Intl.Collator`\-Objekt, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird.  Weitere Informationen zu diesen Parametern finden Sie unter [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) und [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt.  Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Die `localeCompare`\-Methode führt einen gebietsschemaabhängigen Zeichenfolgenvergleich von `stringVar` und `stringExp` durch und gibt abhängig von der Sortierreihenfolge des Standardgebietsschemas eines der folgenden Ergebnisse zurück:  
  
-   \-1, wenn `stringVar` vor `stringExp` steht.  
  
-   \+1, wenn `stringVar` nach `stringExp` steht.  
  
-   0 \(null\), wenn beide Zeichenfolgen gleichwertig sind.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung von `localeCompare` veranschaulicht.  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## Beispiel  
 Der folgende Code zeigt, wie `localeCompare` mit dem Gebietsschema Deutsch \(Deutschland\) verwendet wird.  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie `localeCompare` mit dem Gebietsschema Deutsch \(Deutschland\) und einer gebietsschemaspezifischen Erweiterung verwendet wird, die die Sortierreihenfolge für deutsche Telefonbücher angibt.  Dieses Beispiel veranschaulicht gebietsschemaspezifische Unterschiede.  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../includes/jsv55-md.md)]  
  
 `locales`\- und `options`\-Parameter:  
  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]  
  
## Siehe auch  
 [toLocaleString\-Methode \(Objekt\)](../../javascript/reference/tolocalestring-method-object-javascript.md)