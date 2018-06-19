---
title: ToLocaleString (Anzahl) | Microsoft Docs
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640830"
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Konvertiert eine Zahl mithilfe des aktuellen oder angegebenen Gebietsschemas in eine Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parameter  
 `numberObj`  
 Erforderlich. Das zu konvertierende `Number`-Objekt.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## <a name="remarks"></a>Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleString` zum Vergleichen intern `Intl.NumberFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird. Weitere Informationen zu diesen Parametern finden Sie unter [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt. Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
> [!NOTE]
>  Wenn Sie den `locales`-Parameter weglassen, verwenden Sie `toLocaleString`, um Ergebnisse nur einem Benutzer anzuzeigen. Verwenden Sie ihn nicht, um Werte innerhalb eines Skripts zu berechnen, da das zurückgegebene Ergebnis computerspezifisch ist (die Methode gibt das aktuelle Gebietsschema zurück).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die `toLocaleString`-Methode ohne Parameter verwendet wird.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleString`-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales`- und `options`-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [toLocaleDateString-Methode (Datum)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)