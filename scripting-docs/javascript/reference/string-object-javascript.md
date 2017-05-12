---
title: "String-Objekt (JavaScript) | Microsoft Docs"
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
  - "String_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String-Objekt"
  - "String-Objekt, Übersicht"
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# String-Objekt (JavaScript)
Ermöglicht das Bearbeiten und Formatieren von Textzeichenfolgen und die Bestimmung und Auffindung von untergeordneten Zeichenfolgen in Zeichenfolgen.  
  
## Syntax  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## Parameter  
 `newString`  
 Erforderlich.  Der Variablenname, dem das `String`\-Objekt zugewiesen wird.  
  
 `stringLiteral`  
 Optional.  Eine beliebige Gruppe mit Unicode\-Zeichen.  
  
## Hinweise  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] bietet Escapesequenzen, die Sie in Zeichenfolgen einfügen können, um Zeichen zu erstellen, die Sie nicht direkt tippen können.  So gibt beispielsweise `\t` ein Tabstoppzeichen an.  Weitere Informationen finden Sie unter [Sonderzeichen](../../javascript/advanced/special-characters-javascript.md).  
  
## Zeichenfolgenliterale  
 Ein *Zeichenfolgenliteral* besteht aus null oder mehr Zeichen, die in einfache oder doppelte Anführungszeichen eingeschlossen sind.  Ein Zeichenfolgenliteral hat den primären \(primitiven\) Datentyp `string`.  Ein *String\-Objekt* wird mithilfe des [new\-Operators](../../javascript/reference/new-operator-decrementjavascript.md) erstellt und hat den Datentyp `Object`.  
  
 Das folgende Beispiel zeigt, dass der Datentyp eines Zeichenfolgenliterals nicht der gleiche wie der eines `String`\-Objekts ist.  
  
```javascript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## Methoden für Zeichenfolgenliterale  
 Wenn Sie eine Methode in einem Zeichenfolgenliteral aufrufen, wird es vorübergehend in ein Zeichenfolgenwrapperobjekt konvertiert.  Das Zeichenfolgenliteral wird so behandelt, als wäre es mit dem `new`\-Operator erstellt worden.  
  
 Im folgenden Beispiel wird die `toUpperCase`\-Methode auf ein Zeichenfolgenliteral angewendet.  
  
```javascript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## Zugreifen auf ein einzelnes Zeichen  
 Sie können auf ein einzelnes Zeichen einer Zeichenfolge als schreibgeschützte indizierte Array\-Eigenschaft zugreifen.  Diese Funktion wurde in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] eingeführt.  Im folgenden Beispiel wird auf einzelne Zeichen der Zeichenfolge zugegriffen.  
  
```javascript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## Anforderungen  
 Das `String Object` wurde in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] eingeführt.  Einige Member der folgenden Listen wurden in höheren Versionen eingeführt.  
  
<a name="js56jsobjstringprop"></a>   
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `String`\-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|[constructor\-Eigenschaft](../../javascript/reference/constructor-property-string.md)|Gibt die Funktion an, durch die ein Objekt erstellt wird.|  
|[length\-Eigenschaft \(String\)](../../javascript/reference/length-property-string-javascript.md)|Gibt die Länge eines `String`\-Objekts zurück.|  
|[prototype\-Eigenschaft](../../javascript/reference/prototype-property-string.md)|Gibt einen Verweis auf den Prototyp einer Objektklasse zurück.|  
  
## Funktionen  
 In der folgenden Tabelle werden die Funktionen des `String`\-Objekts aufgeführt.  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[String.fromCharCode\-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)|Gibt eine Zeichenfolge aus einer Reihe von Unicode\-Zeichenwerten zurück.|  
|[String.fromCodePoint\-Funktion](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Gibt die Zeichenfolge zurück, die einem Unicode UTF\-16\-Codepunkt zugeordnet ist.|  
|[String.raw\-Funktion](../../javascript/reference/string-raw-function-javascript.md)|Gibt eine Vorlagenzeichenfolge in Form einer unformatierten Zeichenfolge zurück.|  
  
<a name="js56jsobjstringmeth"></a>   
## Methoden  
 In der folgenden Tabelle werden die Methoden des `String`\-Objekts aufgeführt.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[anchor\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text einen HTML\-Anker mit einem NAME\-Attribut ein.|  
|[big\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<BIG\>\-HTML\-Tags ein.|  
|[blink\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<BLINK\>\-HTML\-Tags ein.|  
|[bold\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<B\>\-HTML\-Tags ein.|  
|[charAt\-Methode](../../javascript/reference/charat-method-string-javascript.md)|Gibt das Zeichen am angegebenen Index zurück.|  
|[charCodeAt\-Methode](../../javascript/reference/charcodeat-method-string-javascript.md)|Gibt die Unicode\-Codierung des angegebenen Zeichens zurück.|  
|[codePointAt\-Methode](../../javascript/reference/codepointat-method-string-javascript.md)|Gibt den Codepunkt eines Unicode\-UTF\-16\-Zeichens zurück.|  
|[concat\-Methode \(String\)](../../javascript/reference/concat-method-string-javascript.md)|Gibt eine Zeichenfolge zurück, die die Verkettung der beiden angegebenen Zeichenfolgen enthält.|  
|[endsWith\-Methode](../../javascript/reference/endswith-method-string-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine Zeichenfolge oder Teilzeichenfolge mit einer anderen angegebenen Zeichenfolge endet.|  
|[includes\-Methode](../../javascript/reference/includes-method-string-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob die übergebene Zeichenfolge im string\-Objekt enthalten ist.|  
|[fixed\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<TT\>\-HTML\-Tags ein.|  
|[fontcolor\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<FONT\>\-HTML\-Tags mit einem COLOR\-Attribut ein.|  
|[fontsize\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<FONT\>\-HTML\-Tags mit einem SIZE\-Attribut ein.|  
|[hasOwnProperty\-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.|  
|[indexOf\-Methode \(String\)](../../javascript/reference/indexof-method-string-javascript.md)|Gibt die Zeichenposition zurück, an der eine Teilzeichenfolge in einer Zeichenfolge zum ersten Mal vorkommt.|  
|[isPrototypeOf\-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt in der Prototypenkette eines anderen Objekts vorhanden ist.|  
|[italics\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<I\>\-HTML\-Tags ein.|  
|[lastIndexOf\-Methode \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Gibt das letzte Vorkommen einer untergeordneten Zeichenfolge in einer Zeichenfolge zurück.|  
|[link\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text einen HTML\-Anker mit einem HREF\-Attribut ein.|  
|[localeCompare\-Methode](../../javascript/reference/localecompare-method-string-javascript.md)|Gibt einen Wert zurück, der angibt, ob zwei Zeichenfolgen im aktuellen Gebietsschema identisch sind.|  
|[match\-Methode](../../javascript/reference/match-method-string-javascript.md)|Sucht eine Zeichenfolge unter Verwendung eines angegebenen **Regular Expression**\-Objekts und gibt das Ergebnis als Array zurück.|  
|[normalize\-Methode](../../javascript/reference/normalize-method-string-javascript.md)|Gibt die Unicode\-Normalisierungsform einer angegebenen Zeichenfolge zurück.|  
|[propertyIsEnumerable\-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine angegebene Eigenschaft Teil eines Objekts ist, und ob sie aufzählbar ist.|  
|[repeat\-Methode](../../javascript/reference/repeat-method-string-javascript.md)|Gibt ein neues String\-Objekt mit einem Wert zurück, der gleich der ursprünglichen Zeichenfolge in der angegebenen Anzahl von Wiederholungen ist.|  
|[replace\-Methode](../../javascript/reference/replace-method-string-javascript.md)|Verwendet einen regulären Ausdruck, um Text in einer Zeichenfolge zu ersetzen und gibt das Ergebnis zurück.|  
|[search\-Methode](../../javascript/reference/search-method-string-javascript.md)|Gibt die Position der ersten übereinstimmenden Teilzeichenfolge in einer Suche mit einem regulären Ausdruck zurück.|  
|[slice\-Methode \(String\)](../../javascript/reference/slice-method-string-javascript.md)|Gibt einen Abschnitt einer Zeichenfolge zurück.|  
|[small\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<SMALL\>\-HTML\-Tags ein.|  
|[split\-Methode](../../javascript/reference/split-method-string-javascript.md)|Gibt das Zeichenfolgenarray zurück, das entsteht, wenn eine Zeichenfolge in Teilzeichenfolgen unterteilt wird.|  
|[startsWith\-Methode](../../javascript/reference/startswith-method-string-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine Zeichenfolge oder Teilzeichenfolge mit einer anderen angegebenen Zeichenfolge endet.|  
|[strike\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<STRIKE\>\-HTML\-Tags ein.|  
|[sub\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<SUB\>\-HTML\-Tags ein.|  
|[substr\-Methode](../../javascript/reference/substr-method-string-javascript.md)|Gibt eine Teilzeichenfolge zurück, die an der angegebenen Position beginnt und eine angegebene Länge hat.|  
|[substring\-Methode](../../javascript/reference/substring-method-string-javascript.md)|Gibt die Teilzeichenfolge zurück, die sich innerhalb eines `String`\-Objekts an der angegebenen Position befindet.|  
|[sup\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Fügt vor und nach dem Text \<SUP\>\-HTML\-Tags ein.|  
|[toLocaleLowerCase\-Methode](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Gibt eine Zeichenfolge zurück, in der alle alphabetischen Zeichen unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung in Kleinbuchstaben konvertiert wurden.|  
|[toLocaleString\-Methode](../../javascript/reference/tolocalestring-method-object-javascript.md)|Gibt ein Objekt zurück, das unter Verwendung des aktuellen Gebietsschemas in eine Zeichenfolge konvertiert wurde.|  
|[toLocaleUpperCase\-Methode](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Gibt eine Zeichenfolge zurück, in der alle alphabetischen Zeichen unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung in Großbuchstaben konvertiert wurden.|  
|[toLowerCase\-Methode](../../javascript/reference/tolowercase-method-javascript.md)|Gibt eine Zeichenfolge zurück, in der alle alphabetischen Zeichen in Kleinbuchstaben konvertiert wurden.|  
|[toString\-Methode](../../javascript/reference/tostring-method-string-1.md)|Gibt die Zeichenfolge zurück.|  
|[toUpperCase\-Methode](../../javascript/reference/touppercase-method-string-javascript.md)|Gibt eine Zeichenfolge zurück, in der alle alphabetischen Zeichen in Großbuchstaben konvertiert wurden.|  
|[trim\-Methode](../../javascript/reference/trim-method-string-javascript.md)|Gibt eine Zeichenfolge zurück, aus der die führenden und nachgestellten Leerstellen\- und Zeilenabschlusszeichen entfernt wurden.|  
|[valueOf\-Methode](../../javascript/reference/valueof-method-string.md)|Gibt die Zeichenfolge zurück.|  
  
## Siehe auch  
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Beispiel\-App für Bildlauf, Schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)