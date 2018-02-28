---
title: DecodeURIComponent-Funktion (JavaScript) | Microsoft Docs
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent-Funktion (JavaScript)
Ruft ab, der nicht codierte Version einer codierten Komponente Uniform Resource Identifier (URI).  
  
## <a name="syntax"></a>Syntax  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `encodedURIString` Argument ist ein Wert, der eine codierte URI-Komponente darstellt.  
  
 Eine URI-Komponente ist Teil einer vollständigen URI.  
  
 Wenn die `encodedURIString` ist ungültig, URIError auftritt.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zuerst codiert und decodiert dann einen URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)