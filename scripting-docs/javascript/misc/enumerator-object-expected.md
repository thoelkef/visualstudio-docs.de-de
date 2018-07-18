---
title: Enumerator-Objekt erwartet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632840"
---
# <a name="enumerator-object-expected"></a>Enumerator-Objekt erwartet
Sie haben versucht, das Aufrufen der **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** oder **Enumerator.prototype.moveNext** Methode für ein Objekt eines anderen Typs als `Enumerator`. Das Objekt dieses Typs des Aufrufs muss vom Typ `Enumerator`. Hier ist ein Beispiel des Codes, die mit dieser Regel beeinträchtigen:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur die **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, oder  **Enumerator.prototype.moveNext** Methoden für Objekte vom Typ `Enumerator`. Um zu ermitteln, ob das Objekt ist ein `Enumerator` -Objekts:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)