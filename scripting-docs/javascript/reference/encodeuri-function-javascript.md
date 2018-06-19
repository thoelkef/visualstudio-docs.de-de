---
title: EncodeURI-Funktion (JavaScript) | Microsoft Docs
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
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636420"
---
# <a name="encodeuri-function-javascript"></a>encodeURI-Funktion (JavaScript)
Codiert eine Zeichenfolge als eine gültige Uniform Resource Identifier (URI)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `URIString` Argument ist ein Wert, der einen codierten URI darstellt.  
  
 Die `encodeURI` Funktion gibt einen codierten URI zurück. Wenn Sie das Ergebnis, das übergeben `decodeURI`, wird die ursprüngliche Zeichenfolge zurückgegeben. Die `encodeURI` Funktion die folgenden Zeichen nicht codiert: ":", "/", ";" und "?". Verwendung `encodeURIComponent` um diese Zeichen zu codieren.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zuerst codiert und decodiert dann einen URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)