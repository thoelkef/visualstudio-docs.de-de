---
title: Objekt (JavaScript)-Funktion | Microsoft Docs
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637370"
---
# <a name="function-object-javascript"></a>Function-Objekt (JavaScript)
Erstellt eine neue Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Syntax  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Parameter  
 `functionName`  
 Erforderlich. Der Name der neu erstellten-Funktion  
  
 `argname1...argnameN`  
 Dies ist optional. Eine Liste von Argumenten, die die Funktion akzeptiert.  
  
 `body`  
 Dies ist optional. Eine Zeichenfolge, den Block enthält [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code ausgeführt werden, wenn die Funktion aufgerufen wird.  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion wird in einen Basisdatentyp [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Syntax 1 wird ein Funktionswert erstellt, die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] konvertiert in eine `Function` Objekt bei Bedarf. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Konvertiert `Function` Objekte, die vom Syntax 2 in Funktionswerte zu dem Zeitpunkt erstellt, die die Funktion aufgerufen wird.  
  
 Syntax 1 ist die Standardmethode zum Erstellen von neuer Funktionen in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Syntax 2 ist eine alternative Form verwendet Funktionsobjekte explizit zu erstellen.  
  
 Beispielsweise um eine Funktion zu deklarieren, die hinzufügt, die zwei Argumente übergeben, möglich Sie es auf zwei Arten:  
  
## <a name="example-1"></a>Beispiel 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Beispiel 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 In beiden Fällen rufen Sie die Funktion mit einer Codezeile etwa wie folgt:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Wenn Sie eine Funktion aufrufen, stellen Sie sicher, dass Sie immer die Klammern und alle erforderlichen Argumente enthalten. Aufrufen einer Funktion ohne Klammern führt dazu, dass die Funktion selbst zurückgegeben werden, statt den Rückgabewert der Funktion.  
  
## <a name="properties"></a>Eigenschaften  
 [0,... n Eigenschaften](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ Arguments-Eigenschaft](../../javascript/reference/arguments-property-function-javascript.md) &#124; [Callee-Eigenschaft](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [Caller-Eigenschaft](../../javascript/reference/caller-property-function-javascript.md) &#124; [Constructor-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md) &#124; [Length-Eigenschaft (Funktion)](../../javascript/reference/length-property-function-javascript.md) &#124; [Prototype-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Methoden  
 [Apply-Methode](../../javascript/reference/apply-method-function-javascript.md) &#124; [Bindungsmethode](../../javascript/reference/bind-method-function-javascript.md) &#124; [Aufrufen der Methode](../../javascript/reference/call-method-function-javascript.md) &#124; [ToString-Methode](../../javascript/reference/tostring-method-object-javascript.md) &#124; [ValueOf-Methode](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Anweisung](../../javascript/reference/function-statement-javascript.md)   
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var-Anweisung](../../javascript/reference/var-statement-javascript.md)