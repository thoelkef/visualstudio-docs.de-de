---
title: "class-Anweisung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# class-Anweisung (JavaScript)
Deklariert eine neue Klasse.  
  
## Syntax  
  
```  
class classname () [extends object] {  
    [constructor([arg1 [,... [,argN]]]) {  
        statements  
    }]  
    [[static] method([arg1 [,... [,argN]]]) {  
        statements  
    }]  
}  
```  
  
#### Parameter  
 `classname`  
 Erforderlich.  Der Name der Klasse.  
  
 `object`  
 Optional.  Ein Objekt oder eine Klasse, von der die neue Klasse Eigenschaften und Methoden erbt.  
  
 `constructor`  
 Optional.  Eine Konstruktorfunktion, die die neue Klasseninstanz initialisiert.  
  
 `arg1...argN`  
 Optional.  Eine optionale durch Trennzeichen getrennte Liste von Argumenten, die die Funktion versteht.  
  
 `statements`  
 Optional.  Eine oder mehrere [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Anweisungen.  
  
 `static`  
 Optional.  Gibt eine statische Methode an.  
  
 `method`  
 Optional.  Eine oder mehrere [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Instanzen oder statische Methoden, die in einer Klasseninstanz aufgerufen werden können.  
  
## Hinweise  
 Mit einer Klasse können Sie neue Objekte mithilfe der prototypbasierten Vererbung sowie mithilfe von Konstruktoren, Instanzmethoden und statischen Methoden erstellen.  Sie können das `super`\-Objekt in einem Klassenkonstruktor oder einer Klassenmethode verwenden, um den gleichen Konstruktor oder die gleiche Methode in der übergeordneten Klassen oder dem übergeordneten Objekt aufzurufen.  Verwenden Sie optional die `extends`\-Anweisung nach dem Klassennamen, um die Klasse oder das Objekt anzugeben, von der bzw. dem die neue Klasse erbt.  
  
## Beispiel  
  
```javascript  
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
  
## Beispiel  
 Sie können auch berechnete Eigenschaftennamen für Klassen erstellen.  Im folgenden Codebeispiel wird eine berechnete Eigenschaft mithilfe der `set`\-Syntax erstellt.  
  
```javascript  
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
  
## Beispiel  
 Im folgenden Codebeispiel wird ein Eigenschaftenname für eine Klasse mithilfe der `get`\-Syntax dynamisch erstellt.  
  
```javascript  
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
  
## Anforderungen  
 [!INCLUDE[jsv12exp](../../includes/jsv12exp-md.md)]