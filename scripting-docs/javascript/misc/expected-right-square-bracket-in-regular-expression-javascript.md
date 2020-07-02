---
title: "\"]\" In regulärem Ausdruck erwartet (JavaScript) | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815629"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ']' erwartet (JavaScript)
Sie haben versucht, eine Zeichenklasse für eine Abgleich mit einem regulären Ausdruck zu erstellen, aber nicht die rechte eckige Klammer. Einzelne literalzeichenkombinationen können in Zeichenklassen zusammengefasst werden, indem Sie in eckige Klammern platziert werden. Eine Zeichenklasse entspricht einem beliebigen Zeichen, das Sie enthält. Beispielsweise entspricht/[abc]/einem beliebigen Buchstaben "a", "b" oder "c".  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie dem regulären Ausdruck die rechte eckige Klammer hinzu.  
  
    > [!NOTE]
    > Wenn eine einzelne eckige Klammer abgeglichen werden soll, versehen Sie Sie mit einem umgekehrten Schrägstrich \\ ([), sodass Sie nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reguläres Ausdrucks Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)