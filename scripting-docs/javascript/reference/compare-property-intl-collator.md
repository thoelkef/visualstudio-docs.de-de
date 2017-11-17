---
title: Compare-Eigenschaft (Intl.Collator) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>compare-Eigenschaft (Intl.Collator)
Gibt eine Funktion, die zwei Zeichenfolgen vergleicht, mit der Sortierreihenfolge des collators verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Parameter  
 `collatorObj`  
 Erforderlich. Der als Name des `Collator`-Objekts, das für den Vergleich verwende werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion, die durch die `compare`-Eigenschaft zurückgegeben wird, akzeptiert zwei Argumente, `x` und `y` und gibt das Ergebnis eines gebietsschemaspezifischen Vergleichs von `x` und `y` zurück, indem sie die Optionen verwendet, die im `Collator`-Objekt angegeben sind.  
  
 Das Ergebnis des Vergleichs ist:  
  
-   -1, wenn `x` vor `y` in der Sortierreihenfolge steht.  
  
-   0 (Null), wenn `x` gleich `y` in der Sortierreihenfolge ist.  
  
-   1, wenn `x` nach `y` in der Sortierreihenfolge steht.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `Collator`-Objekt erstellt und ein Vergleich ausgeführt.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 Im folgenden Beispiel wird ein `Collator`-Objekt zur Suche nach einer Zeichenfolge verwendet.  
  
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
 [Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md)