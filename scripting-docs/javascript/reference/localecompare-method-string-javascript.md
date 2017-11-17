---
title: LocaleCompare-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="localecompare-method-string-javascript"></a>localeCompare-Methode (String) (JavaScript)
Bestimmt, ob zwei Zeichenfolgen im aktuellen Gebietsschema gleich sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Parameter  
 `stringVar`  
 Erforderlich. Die erste zu vergleichende Zeichenfolge.  
  
 `stringExp`  
 Erforderlich. Die zweite zu vergleichende Zeichenfolge.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet. Dieser Parameter muss entsprechen [BCP-47](http://tools.ietf.org/html/rfc5646) Standards; finden Sie unter der [Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md) Details.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen. finden Sie unter der [Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md) Details.  
  
## <a name="remarks"></a>Hinweise  
 Für die Vergleichszeichenfolgen können Sie entweder `String`-Objekte oder Zeichenfolgenliteralen angeben.  
  
 Ab Internet Explorer 11 verwendet `localeCompare` zum Vergleichen intern das `Intl.Collator`-Objekt, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird. Weitere Informationen zu diesen Parametern finden Sie unter [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) und [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt. Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Die `localeCompare`-Methode führt einen gebietsschemaabhängigen Zeichenfolgenvergleich von `stringVar` und `stringExp` durch und gibt abhängig von der Sortierreihenfolge des Standardgebietsschemas eines der folgenden Ergebnisse zurück:  
  
-   -1, wenn `stringVar` vor `stringExp` steht.  
  
-   +1, wenn `stringVar` nach `stringExp` steht.  
  
-   0 (null), wenn beide Zeichenfolgen gleichwertig sind.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung von `localeCompare` veranschaulicht.  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie `localeCompare` mit dem Gebietsschema Deutsch (Deutschland) verwendet wird.  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie `localeCompare` mit dem Gebietsschema Deutsch (Deutschland) und einer gebietsschemaspezifischen Erweiterung verwendet wird, die die Sortierreihenfolge für deutsche Telefonbücher angibt. Dieses Beispiel veranschaulicht gebietsschemaspezifische Unterschiede.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`- und `options`-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [toLocaleString-Methode (Objekt)](../../javascript/reference/tolocalestring-method-object-javascript.md)