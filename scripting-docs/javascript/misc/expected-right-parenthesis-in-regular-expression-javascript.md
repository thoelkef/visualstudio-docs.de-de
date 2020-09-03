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
ms.openlocfilehash: af32127476c83100c0340021428e3abc572ef2f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815641"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ')' erwartet (JavaScript)
Sie haben versucht, eine Erfassung, eine Assertion oder eine Gruppe für reguläre Ausdrücke zu erstellen, jedoch nicht die schließende Klammer. In regulären Ausdrücken haben Klammern mehrere Zwecke. Hauptsächlich werden Sie verwendet, um unter Ausdrücke zu erfassen, Assertionen anzugeben oder Muster zu gruppieren, sodass die Elemente als einzelne Einheit durch *, +,? usw. behandelt werden können.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie die schließenden ganz rechts Klammern hinzu.  
  
    > [!NOTE]
    > Wenn eine einzelne Klammer abgeglichen werden soll, versehen Sie Sie mit einem umgekehrten Schrägstrich \\ (), sodass Sie nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reguläres Ausdrucks Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)