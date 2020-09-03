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
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815278"
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
 [VBArray-Objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)