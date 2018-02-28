---
title: Boolescher Wert erwartet | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Boolescher Wert erwartet
Sie haben versucht, das Aufrufen der **Boolean.prototype.toString** oder **Boolean.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `Boolean`. Das Objekt dieses Typs des Aufrufs muss vom Typ `Boolean`. Zum Beispiel:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur der boolesche Wert**. prototype.toString** oder **Boolean.prototype.valueOf** Methoden für Objekte des Typs **Boolean.**  
  
## <a name="see-also"></a>Siehe auch  
 [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)   
 [Datentypen](../../javascript/data-types-javascript.md)   
 [Steuerung des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Kopieren, Übergeben und Vergleichen von Daten](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)