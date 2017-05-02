---
title: "Verwenden von Konstruktoren zum Definieren von Typen | Microsoft Docs"
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
  - "Konstruktoren, Erstellen"
  - "Erstellen von Objekten, Konstruktorfunktionen"
  - "Funktionen, Konstruktorfunktionen"
  - "Objekte, Erstellen [JavaScript]"
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Verwenden von Konstruktoren zum Definieren von Typen
Ein Konstruktor ist eine Funktion, die ein [Objekt](../../javascript/objects-and-arrays-javascript.md) eines bestimmten Typs instanziiert.  Sie rufen einen Konstruktor mit dem Schlüsselwort **new** auf.  Hier folgen einige Beispiele für Konstruktoren mit integrierten JavaScript\-Objekten und benutzerdefinierten Objekten.  
  
## Beispiele für Konstruktoren  
  
```javascript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 Die Konstruktorfunktion enthält das Schlüsselwort **this**, das ein Verweis auf ein neu erstelltes leeres Objekt ist.  Es initialisiert das neue Objekt, indem Eigenschaften erstellt und diesen Eigenschaften Anfangswerte zugewiesen werden.  Der Konstruktor gibt einen Verweis auf das konstruierte Objekt zurück.  
  
## Schreiben von Konstruktoren  
 Sie können Objekte mithilfe des Operators **new** in Verbindung mit vordefinierten Konstruktorfunktionen wie **Object\(\)**, **Date\(\)** und **Function\(\)** erstellen.  Sie können auch benutzerdefinierte Konstruktorfunktionen erstellen, die eine Gruppe von Eigenschaften und Methoden definieren.  Es folgt ein Beispiel für einen benutzerdefinierten Konstruktor:  
  
```javascript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Wenn Sie den Kreiskonstruktor aufrufen, geben Sie Werte für den Mittelpunkt des Kreises und den Radius ein.  Damit erhalten Sie ein Kreisobjekt, das drei Eigenschaften enthält.  Im Folgenden wird gezeigt, wie Sie ein Kreisobjekt instanziieren.  
  
```javascript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Der Typ aller mit einem benutzerdefinierten Konstruktor erstellten Objekte ist `object`.  Es gibt in JavaScript nur sechs Typen: `object`, `function`, `string`, `number`, `boolean` und `undefined`.  Weitere Informationen finden Sie unter [typeof\-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## Siehe auch  
 [Verwenden der bind\-Methode](../../javascript/advanced/using-the-bind-method-javascript.md)