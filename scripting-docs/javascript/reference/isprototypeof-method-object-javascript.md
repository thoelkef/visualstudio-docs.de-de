---
title: IsPrototypeOf-Methode (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf-Methode (Objekt) (JavaScript)
Bestimmt, ob ein Objekt in der Prototypenkette eines anderen Objekts vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Parameter  
 `prototype`  
 Erforderlich. Ein Objektprototyp.  
  
 `object`  
 Erforderlich. Ein weiteres Objekt, dessen Prototypenkette überprüft werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Die `isPrototypeOf`-Methode gibt `true` zurück, wenn `object` in seiner Prototypenkette `prototype` aufweist. Die Prototypenkette wird verwendet, um die gemeinsame Nutzung von Funktionen zwischen Instanzen desselben Objekttyps zu ermöglichen. Die `isPrototypeOf`-Methode gibt `false` zurück, wenn `object` kein Objekt ist oder wenn das `prototype` nicht in der Prototypenkette von `object` enthalten ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `isPrototypeOf`-Methode veranschaulicht.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)