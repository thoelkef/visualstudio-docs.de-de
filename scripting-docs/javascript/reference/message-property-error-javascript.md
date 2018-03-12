---
title: Message-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>message-Eigenschaft (Fehler) (JavaScript)
Gibt eine Zeichenfolge mit einer Fehlermeldung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Parameter  
 `errorObj`  
 Erforderlich. Instanz des `Error` Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Die `message` Eigenschaft gibt eine Zeichenfolge, eine Fehlermeldung, die einem bestimmten Fehler zugewiesen ist enthält.  
  
 Die `description` und `message` Eigenschaften bieten die gleiche Funktionalität. Die `description` Eigenschaft bietet Abwärtskompatibilität; das `message` Eigenschaft entspricht dem ECMA-Standard.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel bewirkt, dass eine TypeError-Ausnahme ausgelöst wird, und zeigt den Namen des Fehlers und der Meldung.  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Beispiel  
 Die Ausgabe dieses Codes lautet wie folgt.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description-Eigenschaft (Fehler)](../../javascript/reference/description-property-error-javascript.md)   
 [name-Eigenschaft (Fehler)](../../javascript/reference/name-property-error-javascript.md)