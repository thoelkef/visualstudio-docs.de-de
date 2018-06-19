---
title: ToJSON-Methode (Datum) (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641290"
---
# <a name="tojson-method-date-javascript"></a>toJSON-Methode (Datum) (JavaScript)
Anhand der [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) Methode, um die Transformation von Daten für die JavaScript Object Notation (JSON)-Serialisierung eines Objekts zu aktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Parameter  
 `objectname`  
 Erforderlich. Ein Objekt, für welche JSON-Serialisierung erwünscht ist.  
  
## <a name="remarks"></a>Hinweise  
 Die `toJSON` Methode wird verwendet, durch die `JSON.stringify` Funktion. `JSON.stringify`Serialisiert ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Wert in JSON-Text. Wenn eine `toJSON` Methode wird bereitgestellt, um `JSON.stringify`, `toJSON` Methode wird aufgerufen, wenn `JSON.stringify` aufgerufen wird.  
  
 Die `toJSON` Methode ist ein integriertes Mitglied der [Datum](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt. Es gibt eine ISO-formatierte Datumszeichenfolge für die UTC-Zeitzone (gekennzeichnet durch das Suffix Z) zurück.  
  
 Sie überschreiben können die `toJSON` Methode für die `Date` eingeben, oder Definieren einer `toJSON` Methode für andere Objekttypen, die Transformation von Daten für die spezifischen Objekttyps vor der JSON-Serialisierung zu erreichen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `toJSON` -Methode zum Serialisieren der Member der Zeichenfolgenwerte in Großbuchstaben. Die `toJSON` Methode wird aufgerufen, wenn `JSON.stringify` aufgerufen wird.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die `toJSON` -Methode, die Mitglied der integrierten ist die [Datum](../../javascript/reference/date-object-javascript.md) Objekt.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Gilt für:** [Date-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [JSON-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify-Funktion](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript-Methoden](../../javascript/reference/javascript-methods.md)