---
title: ToString-Methode (Boolean) 1 | Microsoft Docs
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640340"
---
# <a name="tostring-method-boolean-1"></a>ToString-Methode (Boolean) 1
Gibt eine Zeichenfolgendarstellung eines Objekts zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>Parameter  
 `boolean`  
 Erforderlich. Ein Objekt, für die eine Zeichenfolgendarstellung abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn der boolesche Wert `true`, gibt "true" zurück. Andernfalls wird "false" zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ToString** Methode.  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]