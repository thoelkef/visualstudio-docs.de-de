---
title: Prototype-Eigenschaft (Array) | Microsoft Docs
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-array"></a>prototype-Eigenschaft (Array)
Gibt einen Verweis auf den Prototyp einer Objektklasse Array zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `array` -Argument ist der Name eines Arrays.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Array`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Array.prototype` hinzu, und verwenden Sie sie dann.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte verfügen über eine `prototype` -Eigenschaft, die schreibgeschützt ist. Eigenschaften und Methoden auf den Prototyp hinzugefügt werden, aber das Objekt möglicherweise nicht anderen Prototyp zugewiesen werden. Jedoch können benutzerdefinierte Objekte als einen neuen Prototyp zugewiesen werden.  
  
 Der Methoden- und Listen für jede systeminterne Objekt in dieser Sprachreferenz anzugeben, welche Teil der Prototyp des Objekts sind und welche ignoriert werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]