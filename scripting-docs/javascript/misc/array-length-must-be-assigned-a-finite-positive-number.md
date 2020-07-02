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
ms.openlocfilehash: 30e02f4f90300e2c05076553419cda5f8c353ab0
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817683"
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
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)