---
title: Die Arraylänge muss eine endliche positive Ganzzahl sein | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348593"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Die Arraylänge muss eine endliche positive Ganzzahl sein.
Sie sind Aufrufen der **Array** Konstruktor mit einem Argument, das keine ganze Zahl ist (ganze Zahlen bestehen aus 0 (null) und den Satz von positiven ganzen Zahlen).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Verwenden von positiven ganzen Zahlen, nur beim Erstellen eines neuen `Array` Objekt. Sollten Sie ein Array mit einem einzelnen Element zu erstellen, die keine ganze Zahl ist, führen Sie es in einem zweistufigen Prozess. Zuerst erstellen Sie ein Array, mit je einem Element und dann fügen Sie den Wert in das erste Element (array[0]). Im folgenden finden ein Beispiel, das diesen Fehler generiert.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Das folgende Beispiel zeigt die korrekte ein Array mit einem einzelnen numerischen Element angeben.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Es gibt keine Obergrenze für die Größe eines Arrays, als der maximal zulässige Ganzzahl-Wert (etwa 4 Milliarden).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)