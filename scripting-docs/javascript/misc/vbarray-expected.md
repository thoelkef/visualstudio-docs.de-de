---
title: VBArray erwartet | Microsoft Docs
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
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633190"
---
# <a name="vbarray-expected"></a>VBArray erwartet
Sie haben ein Objekt, das eine Visual Basic-SafeArray beim nicht nur ein Wert erwartet wurde angegeben.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden. Das SafeArray-Argument ist ein VBArray-Wert und muss einen VBArray-Wert abgerufen haben, vor der Übergabe an die `VBArray` Konstruktor. Dies kann nur durch Abrufen des Werts aus einem vorhandenen ActiveX oder einem anderen Objekt erfolgen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, übergeben Sie nur **VBArray** -Objekte und die **VBArray** Konstruktor.  
  
## <a name="see-also"></a>Siehe auch  
 [VBArray-Objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)