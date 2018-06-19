---
title: Verwenden von Konstruktoren zum Definieren von Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569180"
---
# <a name="using-constructors-to-define-types"></a>Verwenden von Konstruktoren zum Definieren von Typen
Ein Konstruktor ist eine Funktion, die ein [Objekt](../../javascript/objects-and-arrays-javascript.md) eines bestimmten Typs instanziiert. Sie rufen einen Konstruktor mit dem Schlüsselwort **new** auf. Hier folgen einige Beispiele für Konstruktoren mit integrierten JavaScript-Objekten und benutzerdefinierten Objekten.  
  
## <a name="constructor-examples"></a>Beispiele für Konstruktoren  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 Die Konstruktorfunktion enthält das Schlüsselwort **this**, das ein Verweis auf ein neu erstelltes leeres Objekt ist. Es initialisiert das neue Objekt, indem Eigenschaften erstellt und diesen Eigenschaften Anfangswerte zugewiesen werden. Der Konstruktor gibt einen Verweis auf das konstruierte Objekt zurück.  
  
## <a name="writing-constructors"></a>Schreiben von Konstruktoren  
 Sie können Objekte mithilfe des Operators **new** in Verbindung mit vordefinierten Konstruktorfunktionen wie **Object()**, **Date()** und **Function()** erstellen. Sie können auch benutzerdefinierte Konstruktorfunktionen erstellen, die eine Gruppe von Eigenschaften und Methoden definieren. Es folgt ein Beispiel für einen benutzerdefinierten Konstruktor:  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Wenn Sie den Kreiskonstruktor aufrufen, geben Sie Werte für den Mittelpunkt des Kreises und den Radius ein. Damit erhalten Sie ein Kreisobjekt, das drei Eigenschaften enthält. Im Folgenden wird gezeigt, wie Sie ein Kreisobjekt instanziieren.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Der Typ aller mit einem benutzerdefinierten Konstruktor erstellten Objekte ist `object`. Es gibt in JavaScript nur sechs Typen: `object`, `function`, `string`, `number`, `boolean` und `undefined`. Weitere Informationen finden Sie unter [typeof-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden der bind-Methode](../../javascript/advanced/using-the-bind-method-javascript.md)