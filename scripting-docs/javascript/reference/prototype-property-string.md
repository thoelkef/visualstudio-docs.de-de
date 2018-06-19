---
title: Prototype-Eigenschaft (String) | Microsoft Docs
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639180"
---
# <a name="prototype-property-string"></a>prototype-Eigenschaft (String)
Gibt einen Verweis auf den Prototyp einer Objektklasse Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Die `string` -Argument ist der Name einer Zeichenfolge.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Beispielsweise, um eine Methode zum Hinzufügen der `String` -Objekt, das den Wert des letzten Elements der Zeichenfolge zurückgibt, deklarieren Sie die Funktion, fügen Sie diese `String.prototype`, und verwenden.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte verfügen über eine `prototype` -Eigenschaft, die schreibgeschützt ist. Eigenschaften und Methoden auf den Prototyp hinzugefügt werden, aber das Objekt möglicherweise nicht anderen Prototyp zugewiesen werden. Jedoch können benutzerdefinierte Objekte als einen neuen Prototyp zugewiesen werden.  
  
 Der Methoden- und Listen für jede systeminterne Objekt in dieser Sprachreferenz anzugeben, welche Teil der Prototyp des Objekts sind und welche ignoriert werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]