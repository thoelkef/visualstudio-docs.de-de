---
title: Enumeratorobjekt erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572868"
---
# <a name="enumerator-object-expected"></a>Enumerator-Objekt erwartet
Sie haben versucht, die **Enumerator. Prototype. atEnd-, Enumerator. Prototype. Item-, Enumerator. Prototype. muvefirst** -Methode oder **Enumerator. Prototype. mavenext** -Methode für ein Objekt eines anderen Typs als `Enumerator` aufzurufen. Das Objekt dieses Aufruf Typs muss vom Typ "`Enumerator`" sein. Im folgenden finden Sie ein Beispiel für Code, der diese Regel unterbricht:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Rufen Sie nur die **Enumerator. Prototype. atEnd**-, **Enumerator**. Prototype. Item-, **Enumerator. Prototype. muvefirst**-oder **Enumerator. Prototype. Report ext** -Methode für Objekte vom Typ "`Enumerator`" auf. Um herauszufinden, ob es sich bei dem Objekt um ein `Enumerator` Objekt handelt, verwenden Sie Folgendes:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerator-Objekt](../../javascript/reference/enumerator-object-javascript.md)