---
title: Ungültiges Replacer-Argument | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f144e733bf115cc98bf61b23a2ed3e4e3cda1e0
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346214"
---
# <a name="invalid-replacer-argument"></a>Ungültiges replacer-Argument
Wurde versucht, aufzurufen `JSON.stringify` mit einem Argument, das ungültig ist. Die `replacer` -Argument muss eine Funktion oder ein Array sein.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Ändern der `replacer` Argument an eine Funktion oder ein Array.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `memberfilter` ist ein Objekt anstelle einer Funktion oder eines Arrays.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Siehe auch  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)