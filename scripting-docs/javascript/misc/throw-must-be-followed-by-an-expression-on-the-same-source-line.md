---
title: Throw muss durch einen Ausdruck in derselben Quellzeile folgen | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Auf 'throw' muss ein Ausdruck in derselben Quellzeile folgen
Sie verwendet die `throw` -Schlüsselwort, aber nicht es mit einem Ausdruck in derselben Quellzeile folgen. Ein `throw` Anweisung besteht aus zwei Teilen: dem `throw` Schlüsselwort, gefolgt von dem Ausdruck ausgelöst wird. Zum Beispiel:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Sie können nicht diesen beiden Komponenten aufgeteilt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die `throw` -Schlüsselwort und der Ausdruck, der ausgelöst wird, werden in derselben Zeile angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)