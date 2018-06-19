---
title: HasOwnProperty-Methode (Objekt) (JavaScript) | Microsoft Docs
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
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637300"
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty-Methode (Objekt) (JavaScript)
Ermittelt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Instanz eines Objekts.  
  
 `proName`  
 Erforderlich. Zeichenfolgenwert eines Eigenschaftennamens.  
  
## <a name="remarks"></a>Hinweise  
 Die `hasOwnProperty`-Methode gibt `true` zurück, wenn `object` über eine Eigenschaft des angegebenen Namens verfügt, andernfalls `false`. Diese Methode überprüft nicht die Eigenschaften in der Prototypenkette des Objekts; die Eigenschaft muss ein Member des Objekts selbst sein.  
  
 Diese Eigenschaft wird von Hostobjekten für Internet Explorer 8 und ältere Versionen nicht unterstützt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel nutzen alle `String`-Objekte eine gemeinsame split-Methode. Der folgende Code zeigt **"false"** und **"true"**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [in-Operator](../../javascript/reference/in-operator-decrementjavascript.md)