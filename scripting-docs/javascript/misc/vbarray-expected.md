---
title: VBArray erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b4e6521e5d363c21311b19e2ecc1679981acac3
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862697"
---
# <a name="vbarray-expected"></a>VBArray erwartet
Sie haben ein Objekt bereitgestellt, das nicht Visual Basic SafeArray war, als eines erwartet wurde.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Das SAFEARRAY-Argument ist ein VBArray-Wert und muss einen VBArray-Wert abgerufen haben, bevor er an den- `VBArray` Konstruktor übergeben wird. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass Sie nur **VBArray** -Objekte an den **VBArray** -Konstruktor übergeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VBArray-Objekt](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Verwenden von Arrays](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)