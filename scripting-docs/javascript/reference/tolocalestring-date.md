---
title: ToLocaleString (Datum) | Microsoft Docs
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641350"
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Konvertiert ein Datum mithilfe des aktuellen oder angegebenen Gebietsschemas in eine Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Das zu konvertierende `Date`-Objekt.  
  
 `locales`  
 Dies ist optional. Ein Array von Gebietsschemazeichenfolgen, das einen oder mehrere Sprach- oder Gebietsschematags enthält. Wenn Sie mehr als eine Gebietsschemazeichenfolge einschließen, führen Sie sie in absteigender Reihenfolge ihrer Priorität auf, sodass der erste Eintrag das bevorzugte Gebietsschema ist. Wenn Sie diesen Parameter weglassen, wird das Standardgebietsschema der JavaScript-Laufzeit verwendet.  
  
 `options`  
 Dies ist optional. Ein Objekt mit einer oder mehreren Eigenschaften zur Angabe von Vergleichsoptionen.  
  
## <a name="remarks"></a>Hinweise  
 Ab Internet Explorer 11 verwendet `toLocaleString` zum Vergleichen intern `Intl.DateTimeFormat`, durch das Unterstützung für die Parameter `locales` und `options` hinzugefügt wird. Weitere Informationen zu diesen Parametern finden Sie unter [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Die Parameter `locales` und `options` werden nicht in allen Dokumentmodi und Browserversionen unterstützt. Weitere Informationen finden Sie im Abschnitt "Anforderungen".  
  
 Folgendes geschieht, wenn Sie `toLocaleString` im Internet Explorer 10-Standarddokumentmodus, in früheren Dokumentmodi und im Quirksmodus verwenden:  
  
-   Gibt ein `String`-Objekt zurück, in dem das Datum im langen Standardformat des aktuellen Gebietsschemas enthalten ist.  
  
-   Für Tage zwischen 1601 und 1999 wird das Datum entsprechend den Ländereinstellungen formatiert, die in der Systemsteuerung des Benutzers definiert sind.  
  
> [!NOTE]
>  Wenn Sie den `locales`-Parameter weglassen, verwenden Sie `toLocaleString` nur, um die Ergebnisse einem Benutzer anzuzeigen. Verwenden Sie ihn niemals, um Werte innerhalb eines Skripts zu berechnen, da das zurückgegebene Ergebnis computerspezifisch ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toLocaleString`-Methode gezeigt.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toLocaleString`-Methode mit einem angegebenen Gebietsschema und Vergleichsoptionen.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales`- und `options`-Parameter:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [toLocaleDateString-Methode (Datum)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)