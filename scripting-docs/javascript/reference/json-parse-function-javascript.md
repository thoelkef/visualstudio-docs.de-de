---
title: "JSON.parse-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse-Methode"
  - "parse JSON-Methode"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse-Funktion (JavaScript)
Konvertiert eine Zeichenfolge der JSON\-Objekte \(JavaScript\-Objekt\-Notation\) in ein Objekt.  
  
## Syntax  
  
```  
JSON.parse(text [, reviver])  
```  
  
## Parameter  
 `text`  
 Erforderlich. Eine gültige JSON\-Zeichenfolge.  
  
 `reviver`  
 Optional. Eine Funktion, die die Ergebnisse transformiert. Diese Funktion wird für jeden Member des Objekts aufgerufen. Wenn ein Member geschachtelte Objekte enthält, werden die geschachtelten Objekte vor dem übergeordneten Objekt transformiert. Für jeden Member tritt Folgendes auf:  
  
-   Wenn `reviver` einen gültigen Wert zurückgibt, wird der Memberwert durch den umgewandelten Wert ersetzt.  
  
-   Wenn `reviver` denselben Wert zurückgibt, der empfangen wurde, wird der Memberwert nicht geändert.  
  
-   Wenn `reviver` den Wert `Null` oder `Nicht definiert` zurückgibt, wird der Member gelöscht.  
  
## Rückgabewert  
 Ein Objekt oder ein Array.  
  
## Ausnahmen  
 Wenn diese Funktion einen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Parserfehler auslöst \(wie "SCRIPT1014: Ungültiges Zeichen"\), entspricht der Eingabetext nicht JSON\-Syntax. Führen Sie einen der folgenden Schritte aus, um den Fehler zu beheben:  
  
-   Ändern Sie das `text`\-Argument, sodass es JSON\-Syntax entspricht. Weitere Information finden Sie im Thema zur [BNF\-Syntaxschreibweise](http://go.microsoft.com/fwlink/?LinkId=125203) für JSON\-Objekte.  
  
     Wenn die Antwort beispielsweise im JSONP\- anstatt im reinen JSON\-Format vorliegt, versuchen Sie diesen Code auf dem Antwortobjekt:  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Stellen Sie sicher, dass das `text`\-Argument durch eine JSON\-kompatible Implementierung serialisiert wurde, wie `JSON.stringify`.  
  
-   Führen Sie das `text`\-Argument in einem JSON\-Validierungssteuerelement aus, wie beispielsweise [JSLint](http://www.jslint.com/), um das Identifizieren von Syntaxfehlern zu erleichtern.  
  
## Beispiel  
 Im folgenden Beispiel wird `JSON.parse` verwendet, um eine JSON\-Zeichenfolge in ein Objekt zu konvertieren.  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array mit `JSON.stringify` in eine JSON\-Zeichenfolge konvertiert und dann mit `JSON.parse` zurück in ein Array konvertiert wird.  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## Beispiel  
 Die `reviver`\-Funktion wird häufig verwendet, um eine JSON\-Darstellung von Datumszeichenfolgen der International Organisation für Normung \(ISO in `Date`\-Objekte im Format der koordinierten Weltzeit \(UTC\) umzuwandeln. In diesem Beispiel wird `JSON.parse` verwendet, um eine ISO\-formatierte Datumszeichenfolge zu deserialisieren. Die `dateReviver`\-Funktion gibt `Date`\-Objekte für Member zurück, die wie ISO\-Datumszeichenfolgen formatiert werden.  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Siehe auch  
 [JSON.stringify\-Funktion](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON\-Methode \(Datum\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Beispiel\-App für Hubvorlage \(Windows Store\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)