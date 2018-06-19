---
title: EncodeURIComponent-Funktion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636430"
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent-Funktion (JavaScript)
Codiert eine Zeichenfolge als eine wichtige Komponente der Uniform Resource Identifier (URI).  
  
## <a name="syntax"></a>Syntax  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `encodedURIString` Argument ist ein Wert, der eine codierte URI-Komponente darstellt.  
  
 Die `encodeURIComponent` Funktion gibt einen codierten URI zurück. Wenn Sie das Ergebnis, das übergeben `decodeURIComponent`, wird die ursprüngliche Zeichenfolge zurückgegeben. Da die `encodeURIComponent` Funktion werden alle Zeichen codiert, seien Sie vorsichtig, wenn die Zeichenfolge einen Pfad, z. B. darstellt **/folder1/folder2/default.html**. Der Schrägstrich werden codiert und nicht mehr gültig, wenn als eine Anforderung an einen Webserver gesendet. Verwenden der `encodeURI` funktioniert, wenn die Zeichenfolge mehr als eine URI-Komponente enthält.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zuerst eine URI-Komponente codiert und decodiert ihn.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)