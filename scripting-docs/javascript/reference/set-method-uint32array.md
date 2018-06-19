---
title: Set-Methode (Uint32Array) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 00f521b2-db27-45ec-bdee-2891983618b9
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c28d4b8415ef9bab56e3aa0937b051ceb6989f75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639510"
---
# <a name="set-method-uint32array"></a>Set-Methode (Uint32Array)
Legt einen Wert oder ein Wertearray fest.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
uint32Array.set(index, value);  
uint32Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parameter  
 `index`  
 Der Index des festzulegenden Speicherorts.  
  
 `value`  
 Der festzulegende Wert.  
  
 `array`  
 Ein typisiertes oder nicht typisiertes, festzulegendes Array von Werten.  
  
 `offset`  
 Der Index im aktuellen Array, an dem die Werte geschrieben werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Eingabearray ein TypedArray ist, können die beiden Arrays das gleiche zugrunde liegende ArrayBuffer verwenden. In diesem Fall werden die Werte so festgelegt, als ob alle Daten zunächst in einen temporären Puffer kopiert werden, der sich mit keinem der Arrays überschneidet, und anschließend die Daten aus dem temporären Puffer in das aktuelle Array kopiert werden.  
  
 Wenn der Offset plus die Länge des angegebenen Arrays außerhalb des Bereichs für das aktuelle TypedArray liegt, wird eine Ausnahme ausgelöst.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das erste Element des Arrays festgelegt wird.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]