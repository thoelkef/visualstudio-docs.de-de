---
title: Format-Eigenschaft (Intl.NumberFormat) | Microsoft Docs
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>format-Eigenschaft (Intl.NumberFormat)
Gibt eine Funktion zurück, die mithilfe der angegebenen Zahlenformatierungseinstellungen eine gebietsschemaspezifische Zahl formatiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Parameter  
 `numberFormatObj`  
 Erforderlich. Der Name des `NumberFormat`-Objekts, das als Formatierung verwendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Die durch die `format`-Eigenschaft zurückgegebene Funktion akzeptiert ein einzelnes Argument, `value`, und gibt mithilfe der im `NumberFormat`-Objekt angegeben Optionen eine Zeichenfolge zurück, die die lokalisierte Zahl darstellt. Wenn `value` nicht bereitgestellt wird, gibt die Funktion `NaN` (keine Zahl) zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein `NumberFormat`-Objekt zum Erstellen einer lokalisierten Zahl verwendet.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Intl.NumberFormat-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)