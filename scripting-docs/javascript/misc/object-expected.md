---
title: Objekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1611596d844d43ef72663154dc48791830dfe29f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573723"
---
# <a name="object-expected"></a>Objekt erwartet
Sie haben versucht, eine Methode oder Eigenschaft für ein Objekt aufzurufen, dessen Typ nicht `Object` lautete, oder Sie haben ein Argument übergeben, dessen Typ nicht `Object` lautete, als `Object` erforderlich war.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie die Methode oder Eigenschaft nur für Objekte vom Typ `Object` auf.  
  
- Sollte der Fehler für ein Nicht-Objekt-Argument auftreten, übergeben Sie ein Objekt vom Typ `Object`.  
  
- Überprüfen Sie, ob ein nicht definierter oder NULL-Verweis anstelle eines Objekts vom Typ `Object` aufgerufen wird.  
  
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
 [Objekt Objekt](../../javascript/reference/object-object-javascript.md)    
 [Objekte und Arrays](../../javascript/objects-and-arrays-javascript.md)