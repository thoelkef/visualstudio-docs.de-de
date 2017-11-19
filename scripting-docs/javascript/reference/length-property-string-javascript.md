---
title: Length-Eigenschaft (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length-Eigenschaft (String) (JavaScript)
Gibt die Länge eines `String`-Objekts zurück.  
  
> [!WARNING]
>  JavaScript-Zeichenfolgen sind unveränderlich, sodass die Länge einer Zeichenfolge geändert werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Hinweise  
 Die `length` Eigenschaft enthält eine ganze Zahl, die die Anzahl der Zeichen in der `String` Objekt. Das letzte Zeichen in der `String` Objekt besitzt einen Index ich`length` - 1.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Verwendung von `length` veranschaulicht. JavaScript-Zeichenfolgen sind unveränderlich und können nicht direkt bearbeitet werden. Allerdings umgekehrte Zeichenfolge in ein Array zu schreiben und rufen dann `join` mit dem leeren Zeichen, die eine Zeichenfolge ohne Zeichen als Trennzeichen erzeugt.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]