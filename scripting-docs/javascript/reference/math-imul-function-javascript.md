---
title: Math.imul-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638870"
---
# <a name="mathimul-function-javascript"></a>Math.imul-Funktion (JavaScript)
Gibt das Produkt zweier Zahlen zurück, die als 32-Bit-Ganzzahlen mit Vorzeichen behandelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Parameter  
 `x`  
 Erforderlich. Die erste Zahl.  
  
 `y`  
 Erforderlich. Die zweite Zahl.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird für Compiler wie Emscripten und Mandreel verwendet, die die Multiplikation von ganzen Zahlen auf andere Weise implementieren als JavaScript.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Multiplikation von Zahlen mit `Math.imul` veranschaulicht.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]