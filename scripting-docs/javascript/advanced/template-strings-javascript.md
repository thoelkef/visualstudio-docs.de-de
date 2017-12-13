---
title: Vorlagenzeichenfolgen (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>Vorlagenzeichenfolgen (JavaScript)
Mit Vorlagenzeichenfolgen können Sie in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] Zeichenfolgenliterale mit eingebetteten Ausdrücken erstellen. Vorlagenzeichenfolgen bieten außerdem integrierte Unterstützung für mehrzeilige Zeichenfolgen.  
  
 Verwenden Sie zum Erstellen einer Vorlagenzeichenfolge das Graviszeichen (auch Backtick genannt) (`), um die Zeichenfolge anstelle von einfachen oder doppelten Anführungszeichen einzuschließen. Das folgende Codebeispiel veranschaulicht eine einfache Vorlagenzeichenfolge.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Vorlagenzeichenfolgen können Zeilenumbrüche enthalten, ohne dass Zeilenvorschubzeichen (\n) verwendet werden müssen.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Das Dollarzeichen ($) wird zum Angeben von Platzhaltern innerhalb einer Vorlagenzeichenfolge verwendet. Die Syntax lautet ${*expression*}, wobei *expression*, wie im folgenden Beispiel dargestellt, ein JavaScript-Ausdruck ist, z.B. eine Variable oder Funktion.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Markierte Vorlagenfunktionen, mit denen der Wert einer Vorlagenzeichenfolge mithilfe einer mit Argumenten aus der Vorlagenzeichenfolge abgerufenen Funktion geändert werden kann. Das erste Argument ist ein durch Vorlagenzeichenfolgen-Ausdrücke getrenntes Array von Zeichenfolgenliteralen, und das zweite Argument ist ein Array (ein [Rest-Parameter](../../javascript/functions-javascript.md)), der die Werte der Vorlagenzeichenfolgen-Ausdrücke enthält.  
  
 Im folgenden Beispiel wird die markierte Vorlagenfunktion, buildURL, zum Erstellen einer URL verwendet. Für die Syntax gilt, den Funktionsnamen, gefolgt von der Vorlagenzeichenfolge zu verwenden.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Wenn Sie auf die übergebenen Rohzeichenfolgen-Werte zugreifen müssen, unterstützt das an die markierte Vorlagenfunktion übergebene Argument eine `raw`-Eigenschaft, die das nicht formatierte Zeichenfolgenformat der übergebenen Zeichenfolgen zurückgibt.  
  
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
>  Sie können auch die [String.raw](../../javascript/reference/string-raw-function-javascript.md)-Funktion zum Zurückgeben des nicht formatierten Zeichenfolgenformats der Vorlagenzeichenfolge verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Sprachreferenz](../../javascript/javascript-language-reference.md)   
 [Erweitertes JavaScript](../../javascript/advanced/advanced-javascript.md)