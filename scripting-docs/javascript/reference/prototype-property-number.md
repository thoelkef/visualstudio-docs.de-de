---
title: Prototype-Eigenschaft (Zahl) | Microsoft Docs
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639230"
---
# <a name="prototype-property-number"></a>prototype-Eigenschaft (Zahl)
Gibt einen Verweis auf den Prototyp einer Objektklasse Anzahl zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `number` -Argument ist der Name einer Zahl.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Beispielsweise, um eine Methode zum Hinzufügen der `Number` Objekt-Anzahl (ganze Zahl) Ziffern zurückgibt, deklarieren Sie die Funktion, fügen Sie diese `Number.prototype`, und verwenden.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte verfügen über eine `prototype` -Eigenschaft, die schreibgeschützt ist. Eigenschaften und Methoden auf den Prototyp hinzugefügt werden, aber das Objekt möglicherweise nicht anderen Prototyp zugewiesen werden. Jedoch können benutzerdefinierte Objekte als einen neuen Prototyp zugewiesen werden.  
  
 Der Methoden- und Listen für jede systeminterne Objekt in dieser Sprachreferenz anzugeben, welche Teil der Prototyp des Objekts sind und welche ignoriert werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]