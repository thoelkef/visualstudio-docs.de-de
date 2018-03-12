---
title: Trim-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim-Methode (String) (JavaScript)
Entfernt die führenden und nachfolgenden Leerstellen- und Zeilenabschlusszeichen aus einer Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Ein `String`-Objekt oder Zeichenfolgenliteral. Diese Zeichenfolge wird nicht von der `trim`-Methode geändert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die ursprüngliche Zeichenfolge, aus der die führenden und nachfolgenden Leerstellen- und Zeilenabschlusszeichen entfernt wurden.  
  
## <a name="remarks"></a>Hinweise  
 Die entfernten Zeichen umfassen Leerzeichen, Tabulatorzeichen, Seitenvorschübe, Wagenrückläufe und Zeilenvorschübe. Finden Sie unter [Sonderzeichen](../../javascript/advanced/special-characters-javascript.md) für eine umfassende Liste der Leerstellen- und Zeilenabschlusszeichen Zeichen.  
  
 Ein Beispiel, das veranschaulicht, wie eine eigene trim-Methode zu implementieren, finden Sie unter [Prototypen und Prototypvererbung](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `trim`-Methode veranschaulicht.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Sonderzeichen](../../javascript/advanced/special-characters-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)   
 [Beispiel-app für Bildlauf, schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)