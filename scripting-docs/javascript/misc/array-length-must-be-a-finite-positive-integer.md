---
title: Die Array Länge muss eine endliche positive Ganzzahl sein. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b9a85c0c7457cb06d36fd3cd849ce48484b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817085"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Die Arraylänge muss eine endliche positive Ganzzahl sein.
Sie rufen den Arraykonstruktor mit einem Argument auf, **bei dem es** sich nicht um eine ganze Zahl handelt (ganze Zahlen bestehen aus 0 und dem Satz positiver ganzer Zahlen).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Verwenden Sie positive ganze Zahlen nur, wenn Sie ein neues `Array` Objekt erstellen. Wenn Sie ein Array mit einem einzelnen Element erstellen möchten, bei dem es sich nicht um eine ganze Zahl handelt, führen Sie es in einem zweistufigen Prozess aus. Erstellen Sie zunächst ein Array mit einem Element, und legen Sie dann den Wert im ersten Element (Array [0]) ab. Im folgenden Beispiel wird dieser Fehler generiert.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Im folgenden Beispiel wird die richtige Methode zum Angeben eines Arrays mit einem einzelnen numerischen Element veranschaulicht.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Es gibt keine Obergrenze für die Größe eines Arrays, außer den maximalen ganzzahligen Wert (ungefähr 4 Milliarden).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)