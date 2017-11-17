---
title: ToString-Methode (Fehler) | Microsoft Docs
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-error"></a>toString-Methode (Fehler)
Gibt eine Zeichenfolgendarstellung eines Fehlers zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>Parameter  
 `date`  
 Erforderlich. Der Fehler als Zeichenfolge dargestellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt "Fehler:" sowie die Fehlermeldung angezeigt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `toString` Methode mit einem Fehler.  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]