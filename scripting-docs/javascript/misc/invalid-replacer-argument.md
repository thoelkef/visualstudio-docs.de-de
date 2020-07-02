---
title: Ungültiges Replacer-Argument | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 452af60c37e4a56996438cc2957e9b69ccee98ef
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816825"
---
# <a name="invalid-replacer-argument"></a>Ungültiges replacer-Argument
Es wurde versucht, mit einem ungültigen Argument aufzurufen `JSON.stringify` . Das `replacer` Argument muss eine Funktion oder ein Array sein.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Ändern Sie das- `replacer` Argument in eine Funktion oder ein Array.  
  
## <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel verursacht einen Laufzeitfehler, da `memberfilter` ein Objekt anstelle einer Funktion oder eines Arrays ist.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON. Analyse-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)