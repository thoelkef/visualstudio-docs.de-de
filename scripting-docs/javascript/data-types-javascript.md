---
title: Datentypen (JavaScript) | Microsoft-Dokumentation
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
- Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569760"
---
# <a name="data-types-javascript"></a>Datentypen (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] gibt es drei primäre Datentypen, zwei zusammengesetzte Datentypen und zwei spezielle Datentypen.  
  
## <a name="primary-data-types"></a>Primäre Datentypen  
 Die primären (primitiven) Datentypen lauten:  
  
-   Zeichenfolge  
  
-   Anzahl  
  
-   Boolesch  
  
## <a name="composite-data-types"></a>Zusammengesetzte Datentypen  
 Die zusammengesetzten (Verweis-)Datentypen lauten:  
  
-   Objekt  
  
-   Array  
  
## <a name="special-data-types"></a>Spezielle Datentypen  
 Die speziellen Datentypen lauten:  
  
-   Null  
  
-   Nicht definiert  
  
## <a name="string-data-type"></a>String-Datentyp  
 Ein Zeichenfolgenwert ist eine Kette aus null oder mehr miteinander verketteten Unicode-Zeichen (Buchstaben, Ziffern und Satzzeichen). Der Zeichenfolgen-Datentyp dient zur Darstellung von Text in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Sie können Zeichenfolgenliterale in Skripts einfügen, indem Sie sie in Paare einfacher oder doppelter Anführungszeichen einschließen. Doppelte Anführungszeichen können in Zeichenfolgen enthalten sein, die von einfachen Anführungszeichen eingeschlossen sind, und einfache Anführungszeichen können in Zeichenfolgen enthalten sein, die von doppelten Anführungszeichen eingeschlossen sind. Nachstehend sind einige Beispiele für Zeichenfolgen aufgeführt:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Beachten Sie, dass [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] über keinen Typ zur Darstellung eines einzelnen Zeichens verfügt. Um ein einzelnes Zeichen in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] darzustellen, erstellen Sie eine Zeichenfolge, die aus nur einem Zeichen besteht. Eine Zeichenfolge, die keine Zeichen enthält (""), ist eine leere Zeichenfolge (mit der Länge 0).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stellt Escapesequenzen bereit, die Sie in Zeichenfolgen einfügen können, um Zeichen zu erstellen, die nicht direkt eingegeben werden können. So gibt beispielsweise `\t` ein Tabstoppzeichen an. Weitere Informationen finden Sie unter [Sonderzeichen](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Zahlen-Datentyp  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] gibt es keine Unterscheidung zwischen ganzzahligen und Gleitkommawerten; eine [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Zahl kann beides sein (intern stellt [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] alle Zahlen als Gleitkommawerte dar).  
  
### <a name="integer-values"></a>Ganzzahlige Werte  
 Ganzzahlige Werte können positive ganze Zahlen, negative ganze Zahlen und 0 sein. Sie können mit der Basis 10 (dezimal), der Basis 16 (hexadezimal) und der Basis 8 (oktal) dargestellt werden. Die meisten Zahlen in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] werden als Dezimalzahlen geschrieben.  
  
 Hexadezimale („hex“) ganze Zahlen werden mit dem Präfix „0x“ (null und x|X) bezeichnet. Sie können nur die Ziffern 0 bis 9 und die Buchstaben A bis F (entweder in Groß- oder in Kleinschreibung) enthalten. Mit den Buchstaben A bis F werden die Zahlen 10 bis 15 zur Basis 10 als einzelne Ziffern dargestellt. D. h., 0xF ist äquivalent zu 15, und 0x10 ist äquivalent zu 16.  
  
 Oktale ganze Zahlen werden mit einer vorangestellten 0 (Null) bezeichnet. Sie können nur die Ziffern 0 bis 7 enthalten. Eine Zahl mit einer vorangestellten "0", in der die Ziffern "8" und/oder "9" enthalten sind, wird als Dezimalzahl interpretiert.  
  
 Sowohl Hexadezimal- als auch Oktalzahlen können negativ sein, sie können jedoch weder Nachkommastellen besitzen noch in wissenschaftlicher (exponentieller) Notation geschrieben werden.  
  
> [!NOTE]
>  Ab [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)] behandelt die [parseInt-Funktion](../javascript/reference/parseint-function-javascript.md) keine Zeichenfolge mit dem Präfix „0“ als oktale Zahl. Wenn Sie die `parseInt`-Funktion jedoch nicht verwenden, können Zeichenfolgen mit dem Präfix von "0" dennoch als oktale Zahlen interpretiert werden.  
  
### <a name="floating-point-values"></a>Gleitkommawerte  
 Gleitkommawerte können ganze Zahlen mit Nachkommastellen sein. Außerdem besteht die Möglichkeit, sie in wissenschaftlicher Notation auszudrücken. Das heißt, dass mit dem Buchstaben "e" in Groß- oder Kleinschreibung der Wert "zehn hoch" dargestellt wird. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stellt Zahlen mithilfe des 8-Byte-Gleitkommastandards IEEE 754 für die numerische Darstellung dar. Dies bedeutet, dass Sie Zahlen bis maximal 1.79769x10<sup>308</sup> und minimal 5x10<sup>-324</sup> schreiben können. Eine Zahl, die ein Dezimaltrennzeichen und eine einzelne "0" vor dem Dezimaltrennzeichen enthält, wird als dezimale Gleitkommazahl interpretiert.  
  
 Beachten Sie, dass eine Zahl, die mit "0x" oder "00" beginnt und ein Dezimaltrennzeichen enthält, einen Fehler auslöst. Im Folgenden finden Sie einige Beispiele für [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Zahlen.  
  
|Anzahl|Beschreibung|Dezimales Äquivalent|  
|------------|-----------------|------------------------|  
|,0001; 0,0001; 1e-4; 1,0e-4|Vier gleichwertige Gleitkommazahlen.|0.0001|  
|3,45e2|Eine Gleitkommazahl.|345|  
|45|Eine ganze Zahl.|45|  
|0378|Eine ganze Zahl. Die Zahl wird als Dezimalzahl behandelt. Grund: Sie sieht zwar wie eine Oktalzahl aus (sie beginnt mit einer Null), 8 ist aber keine zulässige Oktalziffer.|378|  
|0377|Eine oktale ganze Zahl. Beachten Sie, dass sich der Wert dieser Zahl erheblich von dem der Zahl oben unterscheidet, obwohl er nur um eins niedriger zu sein scheint.|255|  
|0.0001|Eine Gleitkommazahl. Obwohl diese Zahl mit einer Null beginnt, handelt es sich nicht um eine Oktalzahl, da sie ein Dezimalkomma enthält.|0.0001|  
|00.0001|Das ist ein Fehler. Die beiden führenden Nullen kennzeichnen die Zahl als oktale, in oktalen Zahlen ist jedoch keine dezimale Komponente zulässig.|N/A (Compilerfehler)|  
|0Xff|Eine hexadezimale ganze Zahl.|255|  
|0x37CF|Eine hexadezimale ganze Zahl.|14287|  
|0x3e7|Eine hexadezimale ganze Zahl. Beachten Sie, dass der Buchstabe 'e' nicht als Potenzierung behandelt wird.|999|  
|0x3,45e2|Das ist ein Fehler. Hexadezimalzahlen dürfen keine Nachkommastellen besitzen.|N/A (Compilerfehler)|  
  
 Außerdem enthält [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Zahlen mit speziellen Werten. Diese lauten wie folgt:  
  
-   NaN (Not a Number, keine Zahl). Dieser Wert wird verwendet, wenn eine mathematische Operation für ungeeignete Daten durchgeführt wird, z. B. für Zeichenfolgen oder den Wert undefined.  
  
-   Positive Unendlichkeit. Dieser Wert wird verwendet, wenn eine positive Zahl zu groß ist, um in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dargestellt zu werden.  
  
-   Negative Unendlichkeit. Dieser Wert wird verwendet, wenn eine negative Zahl zu groß ist, um in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dargestellt zu werden.  
  
-   Positive und negative 0 (null). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterscheidet zwischen positiver und negativer Null.  
  
## <a name="boolean-data-type"></a>Datentyp "Boolean"  
 Während die Datentypen "Zeichenfolge" und "Zahl" eine praktisch unbegrenzte Anzahl von unterschiedlichen Werten haben können, kann der Boolesche Datentyp nur zwei Werte haben. Dies sind die Literale `true` und `false`. Ein Boolescher Wert ist ein Wahrheitswert: Er drückt die Gültigkeit einer Bedingung aus (d. h. er gibt an, ob die Bedingung erfüllt ist oder nicht).  
  
 Vergleiche, die Sie in Skripts durchführen, liefern stets ein Ergebnis vom Typ Boolesch. Betrachten Sie die folgende [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Codezeile.  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Hier wird überprüft, ob der Wert der Variablen `x` der Zahl 2000 entspricht. Wenn ja, wird der boolesche Wert **TRUE** als Vergleichsergebnis zurückgegeben und der Variablen `y` zugewiesen. Wenn `x` ungleich 2000 ist, ergibt der Vergleich den booleschen Wert `false`.  
  
 Boolesche Werte sind insbesondere in Steuerstrukturen hilfreich. Der folgende Code kombiniert einen Vergleich, der einen Booleschen Wert erzeugt, direkt mit einer Anweisung, die ihn verwendet. Betrachten Sie das folgende [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]-Codebeispiel.  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 Die `if/else`-Anweisung in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] führt eine Aktion aus, Anweisung in JavaScript führt eine Aktion aus, wenn ein Boolescher Wert `true` (`z = z + 1`) ist, und eine andere Aktion, wenn der boolesche Wert `false` (`x = x + 1`) ist.  
  
 Sie können einen beliebigen Ausdruck als Vergleichsausdruck verwenden. Jeder Ausdruck, der 0, Null, nicht definiert oder eine leere Zeichenfolge ergibt, wird als `false` interpretiert. Ein Ausdruck, der einen anderen Wert ergibt, wird als `true` interpretiert. Beispielsweise können Sie einen Ausdruck wie den folgenden verwenden:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Beachten Sie, dass die obige Zeile nicht überprüft, ob `x` gleich `y + z` ist, da nur ein einziges Gleichheitszeichen (Zuweisung) verwendet wird. Stattdessen wird mit dem oben angegebenen Code der Variablen `y + z` der Wert `x` zugewiesen und anschließend überprüft, ob das Ergebnis des gesamten Ausdrucks (der Wert von `x`) Null ist. Um zu überprüfen, ob `x` gleich `y + z` ist, verwenden Sie den folgenden Code.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Weitere Informationen zu Vergleichen finden Sie unter [Steuerung des Programmablaufs](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>Der Datentyp "NULL"  
 Der `null`-Datentyp hat nur einen Wert in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: NULL. Das `null`-Schlüsselwort kann nicht als Name einer Funktion oder Variablen verwendet werden.  
  
 Eine Variable, die `null` enthält, hat keine gültige Zahl oder Zeichenfolge, kein gültiges Array oder Objekt bzw. keinen gültigen Booleschen Wert. Sie können den Inhalt einer Variablen löschen (ohne die Variable selbst zu löschen), indem Sie ihr den Wert `null` zuweisen.  
  
 Beachten Sie, dass in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]`null` nicht (wie in C und C++) mit 0 identisch ist. Der Operator `typeof` in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] meldet bei `null`-Werten, dass diese vom Typ `Object` und nicht vom Typ `null` sind. Dieses möglicherweise irreführende Verhalten wird aus Gründen der Abwärtskompatibilität beibehalten.  
  
## <a name="the-undefined-data-type"></a>Der Datentyp "undefined"  
 Der `undefined`-Wert wird zurückgegeben, wenn Sie eine Objekteigenschaft, die nicht vorhanden ist, oder eine Variable verwenden, die deklariert, der aber nie ein Wert zugewiesen wurde.  
  
 Sie können feststellen, ob eine Variable vorhanden ist, indem Sie sie mit `undefined` vergleichen. Sie können jedoch überprüfen, ob ihr Typ `undefined` ist, indem Sie den Typ der Variablen mit der Zeichenfolge "nicht definiert" vergleichen. Im folgenden Beispiel wird gezeigt, wie ermittelt wird, ob die Variable `x` deklariert wurde:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 Ziehen Sie auch in Betracht, den Wert "nicht definiert" mit `null` zu vergleichen. Dieser Vergleich ist `true`, wenn die `someObject.prop`-Eigenschaft `null` ist oder wenn die `someObject.prop`-Eigenschaft nicht vorhanden ist.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Um sicherzustellen, ob eine Objekteigenschaft vorhanden ist, können Sie den **in**-Operator verwenden:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte und Arrays](../javascript/objects-and-arrays-javascript.md)   
 [typeof-Operator](../javascript/reference/typeof-operator-decrementjavascript.md)