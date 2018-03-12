---
title: Number-Objekt (JavaScript) | Microsoft Docs
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
- Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number-Objekt (JavaScript)
Ein Objekt, das eine Zahl beliebiger Art darstellt. Alle JavaScript-Zahlen sind 64-Bit-Gleitkommazahlen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>Parameter  
 `numObj`  
 Erforderlich. Der Variablenname, dem das `Number`-Objekt zugewiesen wird.  
  
 `value`  
 Erforderlich. Der numerische Wert.  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] erstellt `Number`-Objekte, wenn eine Variable auf einen numerischen Wert festgelegt wird, beispielsweise `var num = 255.336;`. `Number`-Objekte müssen nur selten explizit erstellt werden.  
  
 Das `Number`-Objekt verfügt zusätzlich zu den Eigenschaften und Methoden, die von `Object` geerbt werden, über eigene Eigenschaften und Methoden. Zahlen werden unter bestimmten Umständen in Zeichenfolgen konvertiert, z. B. dann, wenn eine Zahl einer Zeichenfolge hinzugefügt oder mit dieser verkettet wird, sowie mithilfe der `toString`-Methode. Weitere Informationen finden Sie unter [Additionsoperator (+)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript verfügt über mehrere Zahlenkonstanten. Eine vollständige Liste finden Sie unter [Nummerkonstanten](../../javascript/reference/number-constants-javascript.md).  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Number`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[constructor-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md)|Gibt die Funktion an, durch die ein Objekt erstellt wird.|  
|[prototype-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)|Gibt einen Verweis auf den Prototyp einer Objektklasse zurück.|  
  
## <a name="functions"></a>Funktionen  
 Die folgende Tabelle enthält die Funktionen des die `Number` Objekt.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[Number.isFinite-Funktion](../../javascript/reference/number-isfinite-function-number-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Wert endlich ist.|  
|[Number.isInteger-Funktion](../../javascript/reference/number-isinteger-function-number-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Wert eine ganze Zahl ist.|  
|[Number.isNaN-Funktion](../../javascript/reference/number-isnan-function-number-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Wert der reservierte Wert `NaN` ist (keine Zahl).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Gibt einen booleschen Wert, der angibt, ob ein Wert gefahrlos in JavaScript dargestellt werden kann.|  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle enthält die Methoden der `Number` Objekt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[hasOwnProperty-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.|  
|[IsPrototypeOf-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt in der Prototypenhierarchie eines anderen Objekts vorhanden ist.|  
|[propertyIsEnumerable-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine angegebene Eigenschaft Teil eines Objekts ist, und ob sie aufzählbar ist.|  
|[ToExponential-Methode](../../javascript/reference/toexponential-method-number-javascript.md)|Gibt eine Zeichenfolge zurück, die eine in Exponentialnotation dargestellte Zahl enthält.|  
|[ToFixed-Methode](../../javascript/reference/tofixed-method-number-javascript.md)|Gibt eine Zeichenfolge zurück, die eine Zahl in Festkommanotation darstellt.|  
|[ToLocaleString-Methode](../../javascript/reference/tolocalestring-number.md)|Gibt ein Objekt zurück, das anhand des aktuellen Gebietsschemas in eine Zeichenfolge konvertiert wird.|  
|[ToPrecision-Methode](../../javascript/reference/toprecision-method-number-javascript.md)|Gibt eine Zeichenfolge mit einer Zahl zurück, die entweder in Exponentialnotation oder in Festkommanotation mit einer angegebenen Anzahl von Stellen dargestellt wird.|  
|[toString-Methode](../../javascript/reference/tostring-method-object-javascript.md)|Gibt eine Zeichenfolgendarstellung eines Objekts zurück.|  
|[valueOf-Methode](../../javascript/reference/valueof-method-object-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Objekte](../../javascript/reference/javascript-objects.md)   
 [Math-Objekt](../../javascript/reference/math-object-javascript.md)   
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)