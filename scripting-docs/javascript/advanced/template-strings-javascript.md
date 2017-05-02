---
title: "Vorlagenzeichenfolgen (JavaScript) | Microsoft Docs"
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
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Vorlagenzeichenfolgen (JavaScript)
Mit Vorlagenzeichenfolgen können Sie in [!INCLUDE[jsv12text](../../includes/jsv12text-md.md)] Zeichenfolgenliterale mit eingebetteten Ausdrücken erstellen.  Vorlagenzeichenfolgen bieten außerdem integrierte Unterstützung für mehrzeilige Zeichenfolgen.  
  
 Verwenden Sie zum Erstellen einer Vorlagenzeichenfolge das Graviszeichen \(auch Backtick genannt\) \(\`\), um die Zeichenfolge anstelle von einfachen oder doppelten Anführungszeichen einzuschließen.  Das folgende Codebeispiel veranschaulicht eine einfache Vorlagenzeichenfolge.  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 Vorlagenzeichenfolgen können Zeilenumbrüche enthalten, ohne dass Zeilenvorschubzeichen \(\\n\) verwendet werden müssen.  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 Das Dollarzeichen \($\) wird zum Angeben von Platzhaltern innerhalb einer Vorlagenzeichenfolge verwendet.  Die Syntax lautet ${*Ausdruck*}, wobei *Ausdruck* ein JavaScript\-Ausdruck ist, z. B. eine Variable oder Funktion, wie im folgenden Beispiel dargestellt.  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 Markierte Vorlagenfunktionen, mit denen der Wert einer Vorlagenzeichenfolge mithilfe einer mit Argumenten aus der Vorlagenzeichenfolge abgerufenen Funktion geändert werden kann.  Das erste Argument ist ein durch Vorlagenzeichenfolgen\-Ausdrücke getrenntes Array von Zeichenfolgenliteralen, und das zweite Argument ist ein Array \(ein [Rest\-Parameter](../../javascript/functions-javascript.md)\), der die Werte der Vorlagenzeichenfolgen\-Ausdrücke enthält.  
  
 Im folgenden Beispiel wird die markierte Vorlagenfunktion, buildURL, zum Erstellen einer URL verwendet.  Für die Syntax gilt, den Funktionsnamen, gefolgt von der Vorlagenzeichenfolge zu verwenden.  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
 Wenn Sie auf die übergebenen Rohzeichenfolgen\-Werte zugreifen müssen, unterstützt das an die markierte Vorlagenfunktion übergebene Argument eine `raw`\-Eigenschaft, die das nicht formatierte Zeichenfolgenformat der übergebenen Zeichenfolgen zurückgibt.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  Sie können auch die [String.raw](../../javascript/reference/string-raw-function-javascript.md)\-Funktion zum Zurückgeben des nicht formatierten Zeichenfolgenformats der Vorlagenzeichenfolge verwenden.  
  
## Siehe auch  
 [JavaScript\-Sprachreferenz](../../javascript/javascript-language-reference.md)   
 [Erweitertes JavaScript](../../javascript/advanced/advanced-javascript.md)