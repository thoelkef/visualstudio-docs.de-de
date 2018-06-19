---
title: ToLocaleDateString-Methode (Datum) (JavaScript) | Microsoft Docs
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
- toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641280"
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString-Methode (Datum) (JavaScript)
Gibt ein Datum als Zeichenfolge zurück, das dem aktuellen Gebietsschema der Hostumgebung oder dem festgelegten Gebietsschema entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## <a name="remarks"></a>Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleDateString` zum Formatieren des Datums intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird. Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt. Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleDateString` im Internet Explorer 10-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Es wird ein Zeichenfolgenwert mit einem Datum in der aktuellen Zeitzone zurückgegeben.  
  
-   Das zurückgegebene Datum hat das Standardformat des aktuellen Gebietsschemas der Hostumgebung.  
  
 Wenn Sie den `locales`-Parameter weglassen, kann bei der Skripterstellung auf den Rückgabewert dieser Methode nicht vertraut werden, da er sich von Computer zu Computer unterscheidet. Verwenden Sie in diesem Szenario die Methode nur in Text formatieren angezeigt – niemals als Teil einer Berechnung.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleDateString`-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`- und `options`-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToDateString-Methode (Datum)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString-Methode (Datum)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)