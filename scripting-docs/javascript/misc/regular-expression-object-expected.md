---
title: Reguläres Ausdrucksobjekt erwartet | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280311"
---
# <a name="regular-expression-object-expected"></a>Reguläres Ausdrucksobjekt erwartet
Sie haben versucht, rufen Sie die **RegExp.prototype.ToString-Methode** oder **RegExp.prototype.valueOf** Methode für ein Objekt von einem anderen Typ als `RegExp`. Das Objekt dieser Art von Aufruf muss vom Typ `RegExp`.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur die **RegExp.prototype.ToString-Methode** oder **RegExp.prototype.valueOf** Methoden für Objekte vom Typ `RegExp`.  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)