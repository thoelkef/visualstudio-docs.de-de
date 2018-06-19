---
title: Object.is-Funktion (JavaScript) | Microsoft Docs
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638700"
---
# <a name="objectis-function-javascript"></a>Object.is-Funktion (JavaScript)
Gibt einen Wert zurück, der angibt, ob zwei Werte den gleichen Wert besitzen.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>Parameter  
 `value1`  
 Erforderlich. Der erste zu testende Wert.  
  
 `value2`  
 Erforderlich. Der zweite zu testende Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn der Wert dem gleichen Wert entspricht; andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
 Im Gegensatz zu dem  == Operator, erzwingt `Object.is` beim Testen von Werten keine Typen.  
  
 Der von `Object.is` angewendete Vergleich ähnelt dem vom === Operator angewendeten Vergleich, außer dass `Object.is` `Number.isNaN` als den gleichen Wert wie `NaN`. Es behandelt + 0 und -0 ebenfalls als unterschiedliche Werte.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]