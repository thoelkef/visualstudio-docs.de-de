---
title: Date-Objekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572898"
---
# <a name="date-object-expected"></a>Date-Objekt erwartet
Sie haben versucht, die **Date. Prototype. ToString** -oder **Date. Prototype. valueOf** -Methode für ein Objekt eines anderen Typs als `Date`aufzurufen. Das Objekt dieses Aufruf Typs muss vom Typ "`Date`" sein. Beispiel:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur die **Date. Prototype. ToString** -Methode oder die **Date. Prototype. valueOf** -Methode für Objekte vom Typ `Date`auf.  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [getDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)