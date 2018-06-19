---
title: Format-Eigenschaft (Intl.DateTimeFormat) | Microsoft Docs
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636590"
---
# <a name="format-property-intldatetimeformat"></a>format-Eigenschaft (Intl.DateTimeFormat)
Gibt eine Funktion zurück, die mithilfe der angegebenen Formatierungseinstellungen für Datum/Uhrzeit ein gebietsschemaspezifisches Datum formatiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Parameter  
 `dateTimeFormatObj`  
 Erforderlich. Der Name des `DateTimeFormat`-Objekts, das als Formatierung verwendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Die durch die `format`-Eigenschaft zurückgegebene Funktion akzeptiert ein einzelnes Argument, `date`, und gibt mithilfe der im `DateTimeFormat`-Objekt angegeben Optionen eine Zeichenfolge zurück, die das lokalisierte Datum darstellt. Der `date`-Parameter der zurückgegebenen Funktion muss eine Zahl, eine Datumszeichenfolge oder ein `Date`-Objekt sein. Wenn `date` nicht angegeben wird, verwendet die Funktion [Date.now](../../javascript/reference/date-now-function-javascript.md) als Standardeingabewert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `DateTimeFormat`-Objekt verwendet, um das Datum "Dec 1, 2007" für Deutsch zu lokalisieren und neu zu formatieren.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Intl.DateTimeFormat-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)