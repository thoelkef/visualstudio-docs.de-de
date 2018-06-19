---
title: IndexOf-Methode (String) (JavaScript) | Microsoft Docs
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
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637650"
---
# <a name="indexof-method-string-javascript"></a>indexOf-Methode (String) (JavaScript)
Gibt die Position des ersten Vorkommens einer Teilzeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Parameter  
 `strObj`  
 Erforderlich. Ein `String` -Objekt oder Zeichenfolgenliteral.  
  
 `subString`  
 Erforderlich. Die in der Zeichenfolge zu suchende Teilzeichenfolge  
  
 `startIndex`  
 Dies ist optional. Der Index, an dem mit der Suche im `String`-Objekt begonnen werden soll. Ohne diese Angabe wird am Beginn der Zeichenfolge mit der Suche begonnen.  
  
## <a name="remarks"></a>Hinweise  
 Die **IndexOf** Methodenrückgabe den Anfang der Teilzeichenfolge in der `String` Objekt. Wird die Teilzeichenfolge nicht gefunden, ist der Rückgabewert – 1.  
  
 Wenn `startindex` negativ ist, wird für `startindex` der Wert 0 (null) verwendet. Wenn sie größer als der höchste Index ist, wird sie als der höchste Index behandelt.  
  
 Die Suche erfolgt von links nach rechts. Diese Methode ist, andernfalls mit **LastIndexOf**.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **IndexOf** Methode.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [LastIndexOf-Methode (String)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Beispiel-app für Bildlauf, schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)