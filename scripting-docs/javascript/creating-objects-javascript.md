---
title: Erstellen von Objekten (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="creating-objects-javascript"></a>Erstellen von Objekten (JavaScript)
Es gibt verschiedene Möglichkeiten, um eigene Objekte in JavaScript zu erstellen. Sie können ein [Object-Objekt](../javascript/reference/object-object-javascript.md) direkt instanziieren und dann Ihre eigenen Eigenschaften und Methoden hinzufügen. Oder Sie können Ihr Objekt anhand der Objektliteralschreibweise definieren. Sie können ein Objekt auch über eine Konstruktorfunktion definieren. Weitere Informationen zur Verwendung von Konstruktorfunktionen finden Sie unter [Verwenden von Konstruktoren zum Definieren von Typen](../javascript/advanced/using-constructors-to-define-types.md).  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie ein Objekt instanziiert wird und einige Eigenschaften hinzugefügt werden. In diesem Fall weist nur das `pasta`-Objekt die Eigenschaften `grain`, `width` und `shape` auf.  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>Objektliterale  
 Sie können auch die Objektliteralschreibweise nutzen, wenn Sie nur eine Instanz eines Objekts erstellen möchten. Der folgende Code zeigt, wie ein Objekt mit der Objektliteralschreibweise instanziiert wird.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Sie können ein Objektliteral auch innerhalb eines Konstruktors verwenden.  
  
> [!CAUTION]
>  Die unten beschriebenen Features werden nur in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] unterstützt.  
  
 In [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] können Sie ein Objektliteral anhand der Kurzsyntax erstellen.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 Das folgende Beispiel zeigt die Verwendung von Kurzsyntax zum Definieren von Methoden in Objektliteralen.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 Zudem lassen sich Eigenschaftennamen in Objektliteralen in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] dynamisch festlegen. Im folgenden Codebeispiel wird ein Eigenschaftenname für ein Objekt mithilfe der Set-Syntax dynamisch erstellt.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 Im folgenden Codebeispiel wird ein Eigenschaftenname für ein Objekt mithilfe der Get-Syntax dynamisch erstellt.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 Im folgenden Codebeispiel wird eine berechnete Eigenschaft mit [Pfeilfunktionssyntax](../javascript/functions-javascript.md) erstellt, um dem Eigenschaftennamen 42 anzufügen.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```

