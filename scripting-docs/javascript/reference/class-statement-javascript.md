---
title: Class-Anweisung (JavaScript) | Microsoft Docs
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634230"
---
# <a name="class-statement-javascript"></a>class-Anweisung (JavaScript)
Deklariert eine neue Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Parameter  
 `classname`  
 Erforderlich. Der Name der Klasse.  
  
 `object`  
 Dies ist optional. Ein Objekt oder eine Klasse, von der die neue Klasse Eigenschaften und Methoden erbt.  
  
 `constructor`  
 Dies ist optional. Eine Konstruktorfunktion, die die neue Klasseninstanz initialisiert.  
  
 `arg1...argN`  
 Dies ist optional. Eine optionale durch Trennzeichen getrennte Liste von Argumenten, die die Funktion versteht.  
  
 `statements`  
 Dies ist optional. Eine oder mehrere [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Anweisungen.  
  
 `static`  
 Dies ist optional. Gibt eine statische Methode an.  
  
 `method`  
 Dies ist optional. Eine oder mehrere [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Instanzen oder statische Methoden, die in einer Klasseninstanz aufgerufen werden können.  
  
## <a name="remarks"></a>Hinweise  
 Mit einer Klasse können Sie neue Objekte mithilfe der prototypbasierten Vererbung sowie mithilfe von Konstruktoren, Instanzmethoden und statischen Methoden erstellen. Sie können das `super`-Objekt in einem Klassenkonstruktor oder einer Klassenmethode verwenden, um den gleichen Konstruktor oder die gleiche Methode in der übergeordneten Klassen oder dem übergeordneten Objekt aufzurufen. Verwenden Sie optional die `extends`-Anweisung nach dem Klassennamen, um die Klasse oder das Objekt anzugeben, von der bzw. dem die neue Klasse erbt.  
  
## <a name="example"></a>Beispiel  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Beispiel  
 Sie können auch berechnete Eigenschaftennamen für Klassen erstellen. Im folgenden Codebeispiel wird eine berechnete Eigenschaft mithilfe der `set`-Syntax erstellt.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird ein Eigenschaftenname für eine Klasse mithilfe der `get`-Syntax dynamisch erstellt.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]