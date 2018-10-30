---
title: Throw muss durch einen Ausdruck in derselben Quellzeile folgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951053"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Auf 'throw' muss ein Ausdruck in derselben Quellzeile folgen
Sie verwendet die `throw` -Schlüsselwort, aber nicht es mit einem Ausdruck in derselben Quellzeile folgen. Ein `throw` Anweisung besteht aus zwei Teilen: dem `throw` -Schlüsselwort, gefolgt von dem Ausdruck, der ausgelöst wird. Zum Beispiel:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Sie können nicht diese beiden Komponenten aufgeteilt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die `throw` -Schlüsselwort und der Ausdruck, der ausgelöst werden, die in der gleichen Zeile angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Error-Objekt](../../javascript/reference/error-object-javascript.md)   
 [Throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)