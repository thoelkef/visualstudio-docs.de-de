---
title: Enumeratorobjekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862625"
---
# <a name="enumerator-object-expected"></a>Enumerator-Objekt erwartet
Sie haben versucht, die **Enumerator. Prototype. atEnd-, Enumerator. Prototype. Item-, Enumerator. Prototype. muvefirst** -Methode oder **Enumerator. Prototype. mavenext** -Methode für ein Objekt eines anderen Typs als aufzurufen `Enumerator` . Das Objekt dieses Aufruf Typs muss vom Typ sein `Enumerator` . Im folgenden finden Sie ein Beispiel für Code, der diese Regel unterbricht:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur die **Enumerator. Prototype. atEnd**-, **Enumerator**. Prototype. Item-, **Enumerator. Prototype. muvefirst**-oder **Enumerator. Prototype. Report ext** -Methode für Objekte `Enumerator` vom Typ auf. Um herauszufinden, ob es sich bei dem Objekt um ein `Enumerator` Objekt handelt, verwenden Sie Folgendes:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumeratorobjekt](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)