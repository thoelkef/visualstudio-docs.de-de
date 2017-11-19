---
title: ToString-Methode (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>toString-Methode (Objekt) (JavaScript)
Gibt eine Zeichenfolgendarstellung eines Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Parameter  
 `objectname`  
 Erforderlich. Ein Objekt, für die eine Zeichenfolgendarstellung gesucht wird.  
  
 `radix`  
 Dies ist optional. Gibt eine Basis für das Konvertieren von numerischen Werten in Zeichenfolgen. Dieser Wert wird nur für Zahlen verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Die **ToString** Methode ist ein Mitglied aller integrierten [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte. Das Verhalten hängt von den Objekttyp ab:  
  
|Objekt|Verhalten|  
|------------|--------------|  
|Array|Elemente einer `Array` in Zeichenfolgen konvertiert werden. Die resultierenden Zeichenfolgen werden verkettet, durch Kommas getrennt.|  
|Boolesch|Wenn der boolesche Wert **"true"**, gibt "`true`". Andernfalls gibt "`false`".|  
|Datum|Gibt die Textdarstellung des Datums zurück.|  
|Fehler|Gibt eine Zeichenfolge mit der zugehörigen Fehlermeldung zurück.|  
|Funktion|Gibt eine Zeichenfolge im folgenden Format zurück, in denen *Funktionsname* ist der Name der Funktion, deren **ToString** Methode wurde aufgerufen:<br /><br /> `function functionname( ) { [native code] }`|  
|Anzahl|Gibt die Textdarstellung der Zahl zurück.|  
|Zeichenfolge|Gibt den Wert der `String` Objekt.|  
|Standard|Gibt `"[object objectname]"`, wobei `objectname` ist der Name des Objekttyps.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ToString** Methode mit einem Basisargument. Der Rückgabewert der Funktion, die unten wird eine Basis-Konvertierungstabelle.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Gilt für**: [Array-Objekt](../../javascript/reference/array-object-javascript.md)&#124; [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)&#124; [Datum Objekt](../../javascript/reference/date-object-javascript.md)&#124; [Fehlerobjekt](../../javascript/reference/error-object-javascript.md)&#124; [Funktion Objekt](../../javascript/reference/function-object-javascript.md)&#124; [Zahl Objekt](../../javascript/reference/number-object-javascript.md)&#124; [Object-Objekt](../../javascript/reference/object-object-javascript.md)&#124; [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [function-Anweisung](../../javascript/reference/function-statement-javascript.md)