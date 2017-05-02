---
title: "Erstellen von Objekten (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Konstruktorfunktionen"
  - "Konstruktoren, Aufnehmen von Eigenschaften und Methoden"
  - "Erstellen von Objekten"
  - "Erstellen von Objekten, Informationen über Erstellen von Objekten"
  - "Erstellen von Objekten, Konstruktorfunktionen"
  - "Erstellen von Objekten, Prototypen"
  - "Benutzerdefinierte Objekte"
  - "Benutzerdefinierte Objekte, Erstellen"
  - "function-Konstruktor"
  - "Initialisieren von Objekten, Verwenden von Konstruktoren"
  - "Objekte, Erstellen [JavaScript]"
  - "Prototypobjekte"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Erstellen von Objekten (JavaScript)
Es gibt verschiedene Möglichkeiten, um eigene Objekte in JavaScript zu erstellen.  Sie können ein [Object\-Objekt](../javascript/reference/object-object-javascript.md) direkt instanziieren und dann Ihre eigenen Eigenschaften und Methoden hinzufügen.  Oder Sie können Ihr Objekt anhand der Objektliteralschreibweise definieren.  Sie können ein Objekt auch über eine Konstruktorfunktion definieren.  Weitere Informationen zur Verwendung von Konstruktorfunktionen finden Sie unter [Verwenden von Konstruktoren zum Definieren von Typen](../javascript/advanced/using-constructors-to-define-types.md).  
  
## Beispiel  
 Der folgende Code zeigt, wie ein Objekt instanziiert wird und einige Eigenschaften hinzugefügt werden.  In diesem Fall weist nur das `pasta`\-Objekt die Eigenschaften `grain`, `width` und `shape` auf.  
  
```javascript  
var pasta = new Object();  
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
  
## Objektliterale  
 Sie können auch die Objektliteralschreibweise nutzen, wenn Sie nur eine Instanz eines Objekts erstellen möchten.  Der folgende Code zeigt, wie ein Objekt mit der Objektliteralschreibweise instanziiert wird.  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Sie können ein Objektliteral auch innerhalb eines Konstruktors verwenden.  
  
> [!CAUTION]
>  Die unten beschriebenen Features werden nur in [!INCLUDE[jsv12text](../includes/jsv12text-md.md)] unterstützt.  
  
 In [!INCLUDE[jsv12text](../includes/jsv12text-md.md)] können Sie ein Objektliteral anhand der Kurzsyntax erstellen.  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 Das folgende Beispiel zeigt die Verwendung von Kurzsyntax zum Definieren von Methoden in Objektliteralen.  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 Zudem lassen sich Eigenschaftennamen in Objektliteralen in [!INCLUDE[jsv12text](../includes/jsv12text-md.md)] dynamisch festlegen.  Im folgenden Codebeispiel wird ein Eigenschaftenname für ein Objekt mithilfe der Set\-Syntax dynamisch erstellt.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
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
  
 Im folgenden Codebeispiel wird ein Eigenschaftenname für ein Objekt mithilfe der Get\-Syntax dynamisch erstellt.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 Im folgenden Codebeispiel wird eine berechnete Eigenschaft mit [Pfeilfunktionssyntax](../javascript/functions-javascript.md) erstellt, um dem Eigenschaftennamen 42 anzufügen.  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```