---
title: Array-Objekt (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634350"
---
# <a name="array-object-javascript"></a>Array-Objekt (JavaScript)
Unterstützt das Erstellen von Arrays beliebigen Datentyps.  
  
## <a name="syntax"></a>Syntax  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Der Variablenname, dem das `Array`-Objekt zugewiesen wird.  
  
 `size`  
 Dies ist optional. Die Größe des Arrays. Weil Arrays nullbasiert sind, haben erstellte Elemente Indizes von 0 bis `size` -1.  
  
 `element0,...,elementN`  
 Dies ist optional. Die im Array zu platzierenden Elemente. Dies erstellt ein Array mit  *n*  + 1 Elementen und einer `length` von  *n*  + 1. Für diese Syntax müssen Sie mehr als ein Element bereitstellen.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem ein Array erstellt wurde, können Sie auf die einzelnen Elemente des Arrays zugreifen, indem Sie die []-Notation verwenden. Beachten Sie, dass Arrays in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nullbasiert sind.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Sie können eine 32-Bit-Ganzzahl ohne Vorzeichen an den `Array`-Konstruktor übergeben, um die Größe des Arrays anzugeben. Wenn der Wert negativ oder keine ganze Zahl ist, tritt ein Laufzeitfehler auf. Wenn Sie den folgenden Code ausführen, wird dieser Fehler in der Konsole angezeigt.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Wenn ein einzelner Wert an den `Array`-Konstruktor übergeben wird, bei dem es sich nicht um eine Zahl handelt, wird die `length`-Eigenschaft auf 1 festgelegt. Zum einzigen Wert des Elements wird das einzelne übergebene Argument.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 JavaScript-Arrays sind Arrays mit geringer Datendichte, was bedeutet, dass nicht alle Elemente in einem Array Daten enthalten. In JavaScript sind nur die Elemente im Array vorhanden, die tatsächlich Daten enthalten. Dadurch wird der vom Array verwendete Speicherplatz reduziert.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Einige Member der folgenden Listen wurden in höheren Versionen eingeführt. Weitere Informationen finden Sie unter [Versionsinformationen](../../javascript/reference/javascript-version-information.md) oder in der Dokumentation für die einzelnen Mitglieder.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Array`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Constructor-Eigenschaft](../../javascript/reference/constructor-property-array.md)|Gibt die Funktion an, mit der ein Array erstellt wird.|  
|[length-Eigenschaft (Array)](../../javascript/reference/length-property-array-javascript.md)|Gibt einen ganzzahligen Wert zurück, der um eins höher ist als das höchste der in einem Array definierten Elemente.|  
|[Prototype-Eigenschaft](../../javascript/reference/prototype-property-array.md)|Gibt einen Verweis auf den Prototyp eines Arrays zurück.|  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle werden die Funktionen des `Array`-Objekts beschrieben.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[Array.From-Funktion](../../javascript/reference/array-from-function-array-javascript.md)|Gibt ein Array aus einem arrayähnlichen oder iterierbaren Objekt zurück.|  
|[Array.isArray-Funktion](../../javascript/reference/array-isarray-function-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt ein Array ist.|  
|[Array.of-Funktion](../../javascript/reference/array-of-function-array-javascript.md)|Gibt ein Array aus den übergebenen Argumenten zurück.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Array`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[concat-Methode (Array)](../../javascript/reference/concat-method-array-javascript.md)|Gibt ein neues Array zurück, das aus einer Kombination von zwei Arrays besteht.|  
|[Entries-Methode](../../javascript/reference/entries-method-array-javascript.md)|Gibt einen Iterator zurück, der die Schlüssel-Wert-Paare des Arrays enthält.|  
|[every-Methode](../../javascript/reference/every-method-array-javascript.md)|Überprüft, ob eine definierte Rückruffunktion für alle Elemente in einem Array `true` zurückgibt.|  
|[Fill-Methode](../../javascript/reference/fill-method-array-javascript.md)|Füllt ein Array mit einem angegebenen Wert.|  
|[filter-Methode](../../javascript/reference/filter-method-array-javascript.md)|Ruft eine definierte Rückruffunktion für jedes Element eines Arrays auf und gibt ein Array von Werten zurück, für das die Rückruffunktion `true` zurückgibt.|  
|[FindIndex-Methode](../../javascript/reference/findindex-method-array-javascript.md)|Gibt einen Indexwert für das erste Arrayelement zurück, das die in einer Rückruffunktion angegebenen Testkriterien erfüllt.|  
|[forEach-Methode](../../javascript/reference/foreach-method-array-javascript.md)|Ruft eine definierte Rückruffunktion für jedes Element in einem Array auf.|  
|[hasOwnProperty-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.|  
|[indexOf-Methode (Array)](../../javascript/reference/indexof-method-array-javascript.md)|Gibt den Index des ersten Vorkommens eines Werts in einem Array zurück.|  
|[IsPrototypeOf-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt in der Prototypenkette eines anderen Objekts vorhanden ist.|  
|[join-Methode](../../javascript/reference/join-method-array-javascript.md)|Gibt ein `String`-Objekt zurück, das aus allen verketteten Elementen eines Arrays besteht.|  
|[Keys-Methode](../../javascript/reference/keys-method-array-javascript.md)|Gibt einen Iterator zurück, der die Indexwerte des Arrays enthält.|  
|[lastIndexOf-Methode (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|Gibt den Index des letzten Vorkommens eines angegebenen Werts in einem Array zurück.|  
|[map-Methode](../../javascript/reference/map-method-array-javascript.md)|Ruft für jedes Element eines Arrays eine definierte Rückruffunktion auf und gibt ein Array zurück, das die Ergebnisse enthält.|  
|[pop-Methode](../../javascript/reference/pop-method-array-javascript.md)|Entfernt das letzte Element aus einem Array und gibt dieses zurück.|  
|[propertyIsEnumerable-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine angegebene Eigenschaft Teil eines Objekts ist, und ob sie aufzählbar ist.|  
|[push-Methode](../../javascript/reference/push-method-array-javascript.md)|Fügt neue Elemente an ein Array an und gibt die neue Länge des Arrays zurück.|  
|[reduce-Methode](../../javascript/reference/reduce-method-array-javascript.md)|Akkumuliert ein einzelnes Ergebnis durch Aufrufen einer definierten Rückruffunktion für alle Elemente in einem Array. Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.|  
|[reduceRight-Methode](../../javascript/reference/reduceright-method-array-javascript.md)|Akkumuliert ein einzelnes Ergebnis durch Aufrufen einer definierten Rückruffunktion für alle Elemente in einem Array (in absteigender Reihenfolge). Der Rückgabewert der Rückruffunktion ist das akkumulierte Ergebnis und wird als Argument im folgenden Aufruf der Rückruffunktion bereitgestellt.|  
|[reverse-Methode](../../javascript/reference/reverse-method-javascript.md)|Gibt ein `Array`-Objekt mit den Elementen in umgekehrter Reihenfolge zurück.|  
|[shift-Methode](../../javascript/reference/shift-method-array-javascript.md)|Entfernt das erste Element aus einem Array und gibt es zurück.|  
|[slice-Methode (Array)](../../javascript/reference/slice-method-array-javascript.md)|Gibt einen Abschnitt eines Arrays zurück.|  
|[some-Methode](../../javascript/reference/some-method-array-javascript.md)|Überprüft, ob eine definierte Rückruffunktion für alle Elemente in einem Array `true` zurückgibt.|  
|[sort-Methode](../../javascript/reference/sort-method-array-javascript.md)|Gibt ein `Array`-Objekt mit sortierten Elementen zurück.|  
|[splice-Methode](../../javascript/reference/splice-method-array-javascript.md)|Entfernt Elemente aus einem Array und fügt ggf. an ihrer Stelle neue Elemente ein, wobei die gelöschten Elemente zurückgegeben werden.|  
|[toLocaleString-Methode](../../javascript/reference/tolocalestring-method-object-javascript.md)|Gibt anhand des aktuellen Gebietsschemas eine Zeichenfolge zurück.|  
|[ToString-Methode](../../javascript/reference/tostring-method-array.md)|Gibt eine Zeichenfolgendarstellung eines Arrays zurück.|  
|[unshift-Methode](../../javascript/reference/unshift-method-array-javascript.md)|Fügt am Anfang eines Arrays neue Elemente ein.|  
|[ValueOf-Methode](../../javascript/reference/valueof-method-array.md)|Ruft einen Verweis auf das Array ab.|  
|[Values-Methode](../../javascript/reference/values-method-array-javascript.md)|Gibt einen Iterator zurück, der die Werte des Arrays enthält.|  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel-app für Bildlauf, schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)