---
title: Symbol.for-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="symbolfor-function-javascript"></a>Symbol.for-Funktion (JavaScript)
Gibt das Symbol für einen angegebenen Schlüssel zurück. Wenn der Schlüssel nicht vorhanden ist, wird ein neues Symbolobjekt mit dem neuen Schlüssel erstellt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Parameter  
 `key`  
 Erforderlich. Der Schlüssel für das Symbol, der auch als Beschreibung verwendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sucht das Symbol in der globalen Symbolregistrierung. Wenn Sie Symbole als Zeichenfolgen serialisieren, verwenden Sie die globale Symbolregistrierung, um sicherzustellen, dass das richtige Symbol bei allen Suchvorgänge einer bestimmten Zeichenfolge zuordnet ist.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]