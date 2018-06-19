---
title: normalize-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638740"
---
# <a name="normalize-method-string-javascript"></a>normalize-Methode (String) (JavaScript)
Gibt die Unicode-Normalisierungsform einer angegebenen Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das string-Objekt für den Test.  
  
 `form`  
 Dies ist optional. Der Unicode-Normalisierungsformwert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Unicode-Normalisierungsform einer angegebenen Zeichenfolge.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn `form` kein unterstützter Wert ist, wird ein `RangeError` ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `stringObj` keine Zeichenfolge ist, erfolgt eine Konvertierung in eine Zeichenfolge, bevor die Methode versucht, die Unicode-Normalisierungsform der Zeichenfolge zurückzugeben.  
  
 `form`muss werden ein Unicode-Normalisierungsform-Wert "NFC", "NFD", "NFKC" oder "NFKD", entsprechend den Werten für angegebene [Unicode Standard Annex #15](http://www.unicode.org/reports/tr15/). Der Standardwert von `form` ist "NFC".  
  
## <a name="example"></a>Beispiel  
 Die folgenden Codebeispiele veranschaulichen die Verwendung der `normalize`Methode.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]