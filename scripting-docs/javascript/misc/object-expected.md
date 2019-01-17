---
title: Objekt erwartet | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49d66c82081af06bf23a43922629a579a6d6f590
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345785"
---
# <a name="object-expected"></a>Objekt erwartet
Sie haben versucht, eine Methode oder Eigenschaft für ein Objekt aufzurufen, dessen Typ nicht `Object` lautete, oder Sie haben ein Argument übergeben, dessen Typ nicht `Object` lautete, als `Object` erforderlich war.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie die Methode oder Eigenschaft nur für Objekte vom Typ `Object` auf.  
  
-   Sollte der Fehler für ein Nicht-Objekt-Argument auftreten, übergeben Sie ein Objekt vom Typ `Object`.  
  
-   Überprüfen Sie, ob ein nicht definierter oder NULL-Verweis anstelle eines Objekts vom Typ `Object` aufgerufen wird.  
  
     Beispiel: Angenommen dieser Fehler tritt auf myVar im folgenden Code auf:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Sie können stattdessen diesen Code verwenden:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Object-Objekt](../../javascript/reference/object-object-javascript.md)   
 [Objekte und Arrays](../../javascript/objects-and-arrays-javascript.md)