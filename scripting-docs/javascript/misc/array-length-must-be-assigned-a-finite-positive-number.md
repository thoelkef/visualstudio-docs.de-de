---
title: Der Arraylänge muss eine endliche positive Ganzzahl zugewiesen sein | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 39f2720efbcd8defffb9d0c77047a50e57939e95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818046"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Der Arraylänge muss eine endliche positive Ganzzahl zugewiesen sein.
Beim Festlegen der **Länge** -Eigenschaft eines vorhandenen **Array** Objekt angegebene Arraylänge, die keine positive Zahl oder 0 (null). Dieser Fehler tritt auf, wenn Sie einen Wert zuweisen der **Länge** Eigenschaft eine `Array` -Objekt, das negativ ist oder keine Zahl (`NaN`). Beachten Sie, dass [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automatisch Bruchzahlen in ganze Zahlen konvertiert.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Weisen Sie eine positive ganze Zahl, zu der Length-Eigenschaft. Es gibt keine Obergrenze für die Größe eines Arrays, als der maximal zulässige Ganzzahl-Wert (etwa 4 Milliarden). Das folgende Beispiel veranschaulicht die richtige Vorgehensweise zum Festlegen der **Länge** Eigenschaft eine **Array** Objekt.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)