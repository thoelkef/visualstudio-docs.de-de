---
title: Constructor-Eigenschaft (boolesch) | Microsoft Docs
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636010"
---
# <a name="constructor-property-boolean"></a>constructor-Eigenschaft (Boolesch)
Gibt die Funktion, die einen booleschen Wert erstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Parameter  
 `boolean`  
 Der Name des booleschen Werts.  
  
 `value`  
 Dies ist optional. Gibt den Wert des booleschen Werts. Dies kann die Nummern 1 oder 0 (null) sein oder die Zeichenfolgen "True" oder "false".  
  
## <a name="remarks"></a>Hinweise  
 Die `constructor` Eigenschaft enthält einen Verweis auf die Funktion, die Instanzen des Boolean-Objekt erstellt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der Constructor-Eigenschaft.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]