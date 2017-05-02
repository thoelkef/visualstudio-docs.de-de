---
title: "JSON.stringify-Funktion (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "stringify-Methode"
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# JSON.stringify-Funktion (JavaScript)
Konvertiert einen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Wert in eine Zeichenfolge von JSON\-Objekten \(JavaScript Objekt Notation\).  
  
## Syntax  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## Parameter  
 `value`  
 Erforderlich.  Ein zu konvertierender [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Wert, normalerweise ein Objekt oder ein Array.  
  
 `replacer`  
 Dies ist optional.  Eine Funktion oder ein Array zum Transformieren der Ergebnisse.  
  
 Wenn `replacer` eine Funktion ist, ruft `JSON.stringify` diese Funktion auf und übergibt ihr den Schlüssel und den Wert jedes Members.  Der Rückgabewert wird anstelle des ursprünglichen Werts verwendet.  Wenn die Funktion `undefined` zurückgibt, wird der Member ausgeschlossen.  Der Schlüssel für das Stammobjekt ist eine leere Zeichenfolge: "".  
  
 Wenn `replacer` ein Array ist, werden nur Member mit Schlüsselwerten im Array konvertiert.  Die Reihenfolge, in der die Member konvertiert werden, entspricht der Reihenfolge der Schlüssel im Array.  Das `replacer`\-Array wird ignoriert, wenn das `value`\-Argument ebenfalls ein Array ist.  
  
 `space`  
 Dies ist optional.  Fügt dem JSON\-Text des Rückgabewerts Einzug, Leerstellen und Zeilenumbruchzeichen hinzu, um ihn besser lesbar zu machen.  
  
 Wenn `space` ausgelassen wird, wird der Text des Rückgabewerts ohne zusätzliche Leerzeichen generiert.  
  
 Wenn `space` eine Zahl ist, wird der Text des Rückgabewerts mit der angegebenen Anzahl von Leerzeichen auf jeder Ebene eingezogen.  Wenn `space` größer als 10 ist, wird der Text um 10 Leerzeichen eingezogen.  
  
 Wenn `space` eine nicht leere Zeichenfolge ist, wie beispielsweise "\\t", wird der Text des Rückgabewerts mit den Zeichen in der Zeichenfolge auf jeder Ebene eingezogen.  
  
 Wenn `space` eine Zeichenfolge mit mehr als 10 Zeichen ist, werden die ersten 10 Zeichen verwendet.  
  
## Rückgabewert  
 Eine Zeichenfolge, die den JSON\-Text enthält.  
  
## Ausnahmen  
  
|Ausnahme|Bedingung|  
|--------------|---------------|  
|[Ungültiges Ersetzungsargument](../../javascript/misc/invalid-replacer-argument.md)|Das `replacer`\-Argument ist weder eine Funktion noch ein Array.|  
|[Zirkelverweis im Wertargument nicht unterstützt](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|Das `value`\-Argument enthält einen Zirkelverweis.|  
  
## Hinweise  
 Wenn `value` eine `toJSON`\-Methode hat, verwendet die `JSON.stringify`\-Funktion den Rückgabewert dieser Methode.  Wenn der Rückgabewert der `toJSON`\-Methode `undefined` ist, wird der Member nicht konvertiert.  Dies ermöglicht es einem Objekt, seine eigene JSON\-Darstellung zu bestimmen.  
  
 Werte, die keine JSON\-Darstellungen aufweisen, wie `undefined`, werden nicht konvertiert.  In den Objekten werden sie verworfen.  In den Arrays werden sie durch Null ersetzt.  
  
 Zeichenfolgenwerte beginnen und enden mit einem Anführungszeichen.  Alle Unicode\-Zeichen können innerhalb der Anführungszeichen eingeschlossen sein, mit Ausnahme der Zeichen, die mit Escapezeichen versehen werden müssen, indem ein umgekehrter Schrägstrich verwendet wird.  Den folgenden Zeichen muss ein umgekehrter Schrägstrich vorangestellt werden:  
  
-   Anführungszeichen \("\)  
  
-   Umgekehrter Schrägstrich \(\\\)  
  
-   Rücktaste \(b\)  
  
-   Seitenvorschub \(f\)  
  
-   Zeilenumbruch \(n\)  
  
-   Wagenrücklauf \(r\)  
  
-   Horizontaler Tabulator \(t\)  
  
-   Vier hexadezimale Ziffern \(uhhhh\)  
  
## Reihenfolge der Ausführung  
 Wenn eine `toJSON`\-Methode für das `value`\-Argument vorhanden ist, ruft `JSON.stringify` während des Serialisierungsprozesses zuerst die `toJSON`\-Methode auf.  Wenn sie nicht vorhanden ist, wird der ursprüngliche Wert verwendet.  Wenn ein `replacer`\-Argument bereitgestellt wird, wird als Nächstes der Wert \(ursprünglicher Wert oder `toJSON`\-Rückgabewert\) durch den Rückgabewert des `replacer`\-Arguments ersetzt.  Schließlich werden Leerzeichen zu dem auf dem optionalen `space`\-Argument basierenden Wert addiert, um den abschließenden JSON\-Text zu generieren.  
  
## Beispiel  
 In diesem Beispiel wird `JSON.stringify` verwendet, um das `contact`\-Objekt in JSON\-Text zu konvertieren.  Das `memberfilter`\-Array wird so definiert, dass nur die `surname` \- und `phone`\-Member konvertiert werden.  Der `firstname`\-Member wird ausgelassen.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## Beispiel  
 In diesem Beispiel wird `JSON.stringify` mit einem Array verwendet.  Die `replaceToUpper`\-Funktion wandelt jede Zeichenfolge im Array in Großbuchstaben um.  
  
```javascript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## Beispiel  
 In diesem Beispiel wird die `toJSON`\-Methode verwendet, um Zeichenfolgenwerte in Großbuchstaben zu konvertieren.  
  
```javascript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Anforderungen  
 [!INCLUDE[jsv58](../../includes/jsv58-md.md)]  
  
## Siehe auch  
 [JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON\-Methode \(Datum\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Beispiel\-App für Feedreader \(Windows Store\)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)