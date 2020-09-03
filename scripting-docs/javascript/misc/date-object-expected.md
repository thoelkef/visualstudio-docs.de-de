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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817605"
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
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [getDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)