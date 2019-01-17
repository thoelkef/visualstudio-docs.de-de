---
title: VBArray erwartet. | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347462"
---
# <a name="vbarray-expected"></a>VBArray erwartet
Sie haben angegeben, ein Objekt, das eine Visual Basic-SafeArray nicht war, wurde erwartet.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Die SafeArray-Argument ist ein VBArray-Wert und muss einen VBArray-Wert abgerufen haben, vor der Übergabe an die `VBArray` Konstruktor. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, übergeben Sie nur **VBArray** Objekte die **VBArray** Konstruktor.  
  
## <a name="see-also"></a>Siehe auch  
 [VBArray-Objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)