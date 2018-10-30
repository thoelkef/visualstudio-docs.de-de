---
title: Zirkelverweis in Wertargument nicht unterstützt | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949421"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Zirkelverweis in Wertargument nicht unterstützt
Wurde versucht, aufzurufen `JSON.stringify` mit einem Wert, der ungültig ist. Die `value` Argument, ein Array oder Objekt enthält einen Zirkelverweis.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Entfernen Sie den Zirkelverweis aus dem Argument an.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `john` enthält einen Verweis auf `mary` und `mary` enthält einen Verweis auf `john`. um den zirkulären Verweis zu entfernen, entfernen Sie entweder oder verworfen Eigenschaft `brother` aus der `mary` Objekt oder die `sister` Eigenschaft aus der `john` Objekt.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)