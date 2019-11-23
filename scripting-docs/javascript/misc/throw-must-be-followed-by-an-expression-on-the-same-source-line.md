---
title: Auf throw muss ein Ausdruck in derselben Quellzeile folgen. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572752"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Auf 'throw' muss ein Ausdruck in derselben Quellzeile folgen
Sie haben das `throw`-Schlüsselwort verwendet, jedoch nicht mit einem Ausdruck in derselben Quellzeile befolgt. Eine `throw`-Anweisung besteht aus zwei Teilen: dem Schlüsselwort `throw`, gefolgt vom Ausdruck, der ausgelöst werden soll. Beispiel:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Sie können diese beiden Komponenten nicht nach oben aufteilen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass das `throw`-Schlüsselwort und der auszulösenden Ausdruck in derselben Zeile angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler Objekt](../../javascript/reference/error-object-javascript.md)   
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)