---
title: ValueOf-Methode (Fehler) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-error"></a>valueOf-Methode (Fehler)
Gibt den Zeichenfolgenwert eines Fehlers zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>Parameter  
 Die `error` Objekt ist Instanz eines Fehlers.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Zeichenfolge "Fehler:" sowie die Fehlermeldung angezeigt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `valueOF` Methode mit einem Datum.  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]