---
title: ToLocaleTimeString-Methode (Datum) (JavaScript) | Microsoft Docs
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
- toLocaleTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleTimeString method
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77d8ee8fb6757b13da22a3cf3a59d28a105292cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaletimestring-method-date-javascript"></a>toLocaleTimeString-Methode (Datum) (JavaScript)
Gibt eine Zeit als Zeichenfolge zurück, das dem aktuellen Gebietsschema der Hostumgebung oder dem festgelegten Gebietsschema entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## <a name="remarks"></a>Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleTimeString` zum Formatieren der Zeit intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird. Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt. Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleTimeString` im Internet Explorer 10-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Es wird ein Zeichenfolgenwert mit einer Zeit in der aktuellen Zeitzone zurückgegeben.  
  
-   Die zurückgegebene Zeit hat das Standardformat des aktuellen Gebietsschemas der Hostumgebung.  
  
 Wenn Sie den `locales`-Parameter weglassen, kann bei der Skripterstellung auf den Rückgabewert dieser Methode nicht vertraut werden, da er sich von Computer zu Computer unterscheidet. Verwenden Sie in diesem Szenario die Methode nur in Text formatieren angezeigt – niemals als Teil einer Berechnung.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleTimeString`-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`- und `options`-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToTimeString-Methode (Datum)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString-Methode (Datum)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)