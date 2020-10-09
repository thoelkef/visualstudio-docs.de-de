---
title: "\")\" In regulärem Ausdruck erwartet (JavaScript) | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b25b5ab48ffe0a9a9dfafa9e60d66913c5e25e
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861895"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ')' erwartet (JavaScript)
Sie haben versucht, eine Erfassung, eine Assertion oder eine Gruppe für reguläre Ausdrücke zu erstellen, jedoch nicht die schließende Klammer. In regulären Ausdrücken haben Klammern mehrere Zwecke. Hauptsächlich werden Sie verwendet, um unter Ausdrücke zu erfassen, Assertionen anzugeben oder Muster zu gruppieren, sodass die Elemente als einzelne Einheit durch *, +,? usw. behandelt werden können.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie die schließenden ganz rechts Klammern hinzu.  
  
    > [!NOTE]
    > Wenn eine einzelne Klammer abgeglichen werden soll, versehen Sie Sie mit einem umgekehrten Schrägstrich \\ (), sodass Sie nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reguläres Ausdrucks Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntax für reguläre Ausdrücke (JavaScript)](/previous-versions/1400241x(v=vs.100))