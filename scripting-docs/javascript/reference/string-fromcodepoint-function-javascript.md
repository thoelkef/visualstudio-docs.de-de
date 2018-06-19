---
title: String.fromCodePoint-Funktion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0905b392606bec9fb59b08a04129ce30cb013db1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639260"
---
# <a name="stringfromcodepoint-function-javascript"></a>String.fromCodePoint-Funktion (JavaScript)
Gibt die Zeichenfolge zurück, die einem Unicode UTF-16-Codepunkt zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### <a name="parameters"></a>Parameter  
 `...codePoints`  
 Erforderlich. Ein Rest-Parameter, der ein oder mehrere UTF-16-Codepunktwerte angibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion löst die Ausnahme `RangeError` aus, wenn `...codePoints` kein gültiger UTF-16-Codepunkt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `fromCodePoint`-Funktion veranschaulicht.  
  
```JavaScript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]