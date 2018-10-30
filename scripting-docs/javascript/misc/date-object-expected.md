---
title: Date-Objekt erwartet | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947640"
---
# <a name="date-object-expected"></a>Date-Objekt erwartet
Sie haben versucht, rufen Sie die **Date.prototype.toString** oder **Date.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `Date`. Das Objekt dieser Art von Aufruf muss vom Typ `Date`. Zum Beispiel:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur die **Date.prototype.toString** oder **Date.prototype.valueOf** Methoden für Objekte vom Typ `Date`.  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [GetDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)