---
title: Date-Objekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862647"
---
# <a name="date-object-expected"></a>Date-Objekt erwartet
Sie haben versucht, die **Date. Prototype. ToString** -oder **Date. Prototype. valueOf** -Methode für ein Objekt eines anderen Typs als aufzurufen `Date` . Das Objekt dieses Aufruf Typs muss vom Typ sein `Date` . Beispiel:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur die **Date. Prototype. ToString** -oder **Date. Prototype. valueOf** -Methode für Objekte vom Typ auf `Date` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate-Methode (Datum)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Systeminterne Objekte](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)