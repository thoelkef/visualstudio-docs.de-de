---
title: Length-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637830"
---
# <a name="length-property-function-javascript"></a>length-Eigenschaft (Funktion) (JavaScript)
Ruft die Anzahl der für eine Funktion definierten Argumente.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche *Funktionsname* ist der Name der Funktion.  
  
 Die **Länge** Eigenschaft einer Funktion wird vom Skriptmodul auf die Anzahl von Argumenten in der Definition der Funktion initialisiert, wenn eine Instanz der Funktion erstellt wird.  
  
 Was geschieht, wenn eine Funktion, mit einer Anzahl von Argumenten, die ungleich dem Wert von aufgerufen wird dessen **Länge** Eigenschaft hängt von der Funktion.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Länge** Eigenschaft:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arguments-Eigenschaft (Funktion)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length-Eigenschaft (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length-Eigenschaft (String)](../../javascript/reference/length-property-string-javascript.md)