---
title: DecodeURI-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>decodeURI-Funktion (JavaScript)
Ruft die decodierte Version einer codierten Uniform Resource Identifier (URI) ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `URIstring` Argument ist ein Wert, der einen codierten URI darstellt.  
  
 Verwenden der `decodeURI` anstelle der veralteten Funktion `unescape` Funktion.  
  
 Die `decodeURI` Funktion gibt einen Zeichenfolgenwert zurück.  
  
 Wenn die `URIString` ist ungültig, URIError auftritt.  
  
 **Gilt für**: [Global-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zuerst eine URI-Komponente codiert und decodiert ihn.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [DecodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [EncodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global-Objekt](../../javascript/reference/global-object-javascript.md)