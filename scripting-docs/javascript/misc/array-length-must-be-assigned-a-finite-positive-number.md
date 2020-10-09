---
title: Der Array Länge muss eine endliche positive Zahl zugewiesen werden | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e0016c7a0a6acb3f08121d8636ccdf848dcf201
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862812"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Der Arraylänge muss eine endliche positive Ganzzahl zugewiesen sein.
Beim Festlegen der **length** -Eigenschaft eines vorhandenen **Array** Objekts haben Sie eine Array Länge angegeben, die keine positive Zahl oder 0 (null) war. Dieser Fehler tritt auf, wenn Sie der **length** -Eigenschaft eines `Array` Objekts, das negativ oder keine Zahl ist (), einen Wert zuweisen `NaN` . Beachten Sie, dass [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Bruchzahlen von automatisch in ganze Zahlen konvertiert werden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Weisen Sie der length-Eigenschaft eine positive ganze Zahl zu. Es gibt keine Obergrenze für die Größe eines Arrays, außer den maximalen ganzzahligen Wert (ungefähr 4 Milliarden). Im folgenden Beispiel wird die richtige Methode zum Festlegen der **length** -Eigenschaft eines **Array** Objekts veranschaulicht.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Arrays](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)