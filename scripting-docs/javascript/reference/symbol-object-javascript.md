---
title: Symbol-Objekt (JavaScript) | Microsoft Docs
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="symbol-object-javascript"></a>Symbol-Objekt (JavaScript)
Ermöglicht Ihnen, einen eindeutigen Bezeichner zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>Parameter  
 `desc`  
 Dies ist optional. Die Beschreibung des Symbols.  
  
## <a name="remarks"></a>Hinweise  
 Mit Symbol-Objekten können Eigenschaften zu vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.  
  
 "Symbol" ist ein primitiver Datentyp. Symbol-Objekte können nicht mit dem `new`-Operator erstellt werden.  
  
 Zum Hinzufügen von Symbol-Objekten zur globalen Symbolregistrierung verwenden Sie die Funktionen `Symbol.for` und `Symbol.keyFor`. Wenn Sie Symbole als Zeichenfolgen serialisieren, verwenden Sie die globale Symbolregistrierung, um sicherzustellen, dass das richtige Symbol bei allen Suchvorgänge einer bestimmten Zeichenfolge zuordnet ist.  
  
 JavaScript umfasst die folgenden integrierten Symbolwerte, die global verfügbar sind.  
  
|Symbol|Beschreibung|  
|------------|-----------------|  
|`Symbol.hasInstance`|Diese Methode bestimmt, ob ein konstruktorobjekt ein Objekt als eine der Instanzen des Konstruktors erkennt. Sie wird intern vom `instanceof`-Operator verwendet.|  
|`Symbol.isConcatSpreadable`|Diese Eigenschaft gibt einen booleschen Wert zurück, der angibt, ob ein Objekt mithilfe von `Array.concat` auf seine Arrayelemente reduziert werden sollte.|  
|`Symbol.iterator`|Diese Methode gibt den Standarditerator eines Objekts zurück. Sie wird intern von der `for...of`-Anweisung verwendet.|  
|`Symbol.toPrimitive`|Diese Methode konvertiert ein Objekt in einen entsprechenden primitiven Wert. Sie wird intern vom abstrakten Vorgang `ToPrimitive` verwendet.|  
|`Symbol.toStringTag`|Diese Eigenschaft gibt einen Zeichenfolgenwert zurück, der verwendet wird, um die standardmäßige Zeichenfolgenbeschreibung eines Objekts zu erstellen. Sie wird intern von der integrierten `Object.toString`-Methode verwendet.|  
|`Symbol.unscopables`|Diese Eigenschaft gibt ein Objekt zurück, dessen Eigenschaften von den `with`-Umgebungsbindungen des zugeordneten Objekts ausgeschlossen sind.|  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle werden die Funktionen des `Symbol`-Objekts aufgelistet.  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|Gibt das Symbol für einen angegebenen Schlüssel zurück. Wenn der Schlüssel nicht vorhanden ist, wird ein neues Symbolobjekt mit dem neuen Schlüssel erstellt.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Gibt den Schlüssel eines angegebenen Symbols zurück.|  
|||  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]