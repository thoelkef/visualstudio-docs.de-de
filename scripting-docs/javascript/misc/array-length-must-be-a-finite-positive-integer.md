---
title: "Die Arraylänge muss eine endliche positive Ganzzahl sein | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Die Arraylänge muss eine endliche positive Ganzzahl sein.
Aufrufen von werden die **Array** Konstruktor mit einem Argument, die keine ganze Zahl ist (ganze Zahlen bestehen aus 0 (null) sowie den Satz von positiven ganzen Zahlen).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden von positiven ganzen Zahlen nur beim Erstellen eines neuen `Array` Objekt. Wenn Sie möchten ein Array mit einem einzelnen Element zu erstellen, die nicht auf eine ganze Zahl ist, führen Sie es in ein zweistufiger Prozess. Zunächst erstellen Sie ein Array mit einem Element, und fügen Sie den Wert in das erste Element (array[0]). Im folgenden finden ein Beispiel, das diesen Fehler generiert.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Das folgende Beispiel veranschaulicht die richtige Methode ein Array mit einem einzelnen numerischen Element angeben.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Es gibt keine Obergrenze für die Größe eines Arrays, als der maximale Ganzzahlwert (ca. 4 Milliarden).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)