---
title: Diese Anweisung (JavaScript) | Microsoft Docs
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
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640320"
---
# <a name="this-statement-javascript"></a>this-Anweisung (JavaScript)
Verweist auf das aktuelle Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Hinweise  
 Das erforderliche `property`-Argument ist eine der Eigenschaften des aktuellen Objekts  
  
 Das `this`-Schlüsselwort kann in den Objektkonstruktoren verwendet werden, um auf das aktuelle Objekt zu verweisen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel **dies** bezieht sich auf das neu erstellte Car-Objekt, und weist drei Eigenschaften Werte zu:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Die **dies** -Schlüsselwort bezeichnet im Allgemeinen die **Fenster** Objekt, wenn es außerhalb des Bereichs aller anderen Objekte verwendet. Innerhalb eines Ereignishandlers bezeichnet `this` jedoch das DOM-Element, das das Ereignis ausgelöst hat.  
  
 Im folgenden Code (für Internet Explorer 9 und höher) gibt der Ereignishandler die Zeichenfolgenversion einer Schaltfläche mit der ID "Clicker" aus.  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Verwenden der bind-Methode](../../javascript/advanced/using-the-bind-method-javascript.md)