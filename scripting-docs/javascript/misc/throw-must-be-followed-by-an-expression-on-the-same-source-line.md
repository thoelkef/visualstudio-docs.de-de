---
title: Auf throw muss ein Ausdruck in derselben Quellzeile folgen. Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815525"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Auf 'throw' muss ein Ausdruck in derselben Quellzeile folgen
Sie haben das `throw` Schlüsselwort verwendet, aber es nicht mit einem Ausdruck in derselben Quellzeile befolgt. Eine- `throw` Anweisung besteht aus zwei Teilen: dem- `throw` Schlüsselwort, gefolgt vom Ausdruck, der ausgelöst werden soll. Beispiel:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Sie können diese beiden Komponenten nicht nach oben aufteilen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass das `throw` -Schlüsselwort und der auszulösenden Ausdruck in derselben Zeile angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [Throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [Try... catch... Abschließend-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)