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
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050508"
---
# <a name="date-object-expected"></a>Date-Objekt erwartet
Sie haben versucht, rufen Sie die **Date.prototype.toString** oder **Date.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `Date`. Das Objekt dieser Art von Aufruf muss vom Typ `Date`. Zum Beispiel:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur die **Date.prototype.toString** oder **Date.prototype.valueOf** Methoden für Objekte vom Typ `Date`.  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [GetDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)