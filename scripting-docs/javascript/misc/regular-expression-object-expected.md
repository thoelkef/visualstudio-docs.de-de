---
title: Reguläres Ausdrucksobjekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b27c90a0c2461d500f618fbf7acede4d6942781
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840671"
---
# <a name="regular-expression-object-expected"></a>Reguläres Ausdrucksobjekt erwartet
Sie haben versucht, rufen Sie die **RegExp.prototype.ToString-Methode** oder **RegExp.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `RegExp`. Das Objekt dieser Art von Aufruf muss vom Typ `RegExp`.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur die **RegExp.prototype.ToString-Methode** oder **RegExp.prototype.valueOf** Methoden für Objekte vom Typ `RegExp`.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)