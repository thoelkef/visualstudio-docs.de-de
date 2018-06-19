---
title: Error-Objekt (JavaScript) | Microsoft Docs
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
- Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637100"
---
# <a name="error-object-javascript"></a>Error-Objekt (JavaScript)
Enthält Informationen über Fehler.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Parameter  
 `errorObj`  
 Erforderlich. Der Variablenname, dem das `Error`-Objekt zugewiesen wird. Die Variablenzuweisung wird ausgelassen, wenn Sie den Fehler mithilfe einer `throw`-Anweisung erstellen.  
  
 `number`  
 Dies ist optional. Numerischer Wert, der einem Fehler zugewiesen wird. Null (0), wenn das Argument ausgelassen wird.  
  
 `description`  
 Dies ist optional. Kurze Zeichenfolge, in der ein Fehler beschrieben wird. Eine leere Zeichenfolge, falls das Argument ausgelassen wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Laufzeitfehler auftritt, wird für die Fehlerbeschreibung eine Instanz des `Error`-Objekts erstellt. Diese Instanz hat zwei systeminterne Eigenschaften, in denen die Beschreibung des Fehlers (`description`-Eigenschaft) und der Fehlernummer (`number`- Eigenschaft) enthalten sind. Weitere Informationen finden Sie unter [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md).  
  
 Eine Fehlernummer ist ein 32-Bit-Wert. Das obere 16-Bit-Wort ist der Einrichtungscode, während das untere Wort den eigentlichen Fehlercode darstellt.  
  
 Unter Verwendung der oben aufgeführten Syntax können `Error`-Objekte auch explizit erstellt oder mithilfe der `throw`-Anweisung ausgelöst werden. In beiden Fällen können Sie beliebige Eigenschaften hinzufügen, um die Funktion des `Error`-Objekts zu erweitern.  
  
 In der Regel die lokale Variable, die in erstellt haben, wird eine **try…catch** Anweisung verweist auf das implizit erstellte `Error` Objekt. Fehlernummer und -beschreibung können daher beliebig verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des `Error`-Objekts.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des implizit erstellten `Error`-Objekts veranschaulicht.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Methoden  
 [ToString-Methode (Fehler)](../../javascript/reference/tostring-method-error.md) &#124; [ValueOf-Methode (Datum)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Eigenschaften  
 [Constructor-Eigenschaft (Fehler)](../../javascript/reference/constructor-property-error.md) &#124; [Description-Eigenschaft](../../javascript/reference/description-property-error-javascript.md) &#124; [message-Eigenschaft](../../javascript/reference/message-property-error-javascript.md) &#124; [-Nameneigenschaft](../../javascript/reference/name-property-error-javascript.md) &#124; [number-Eigenschaft](../../javascript/reference/number-property-error-javascript.md) &#124; [Prototype-Eigenschaft (Fehler)](../../javascript/reference/prototype-property-error.md) &#124; [stack-Eigenschaft (Fehler)](../../javascript/reference/stack-property-error-javascript.md) &#124; [StackTraceLimit-Eigenschaft (Fehler)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try … try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Var-Anweisung](../../javascript/reference/var-statement-javascript.md)   
 [HiLo JavaScript-Beispiel-app (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)