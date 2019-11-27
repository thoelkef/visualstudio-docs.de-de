---
title: "\"]\" In regulärem Ausdruck erwartet (JavaScript) | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576484"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ']' erwartet (JavaScript)
Sie haben versucht, eine Zeichenklasse für eine Abgleich mit einem regulären Ausdruck zu erstellen, aber nicht die rechte eckige Klammer. Einzelne literalzeichenkombinationen können in Zeichenklassen zusammengefasst werden, indem Sie in eckige Klammern platziert werden. Eine Zeichenklasse entspricht einem beliebigen Zeichen, das Sie enthält. Beispielsweise entspricht/[abc]/einem beliebigen Buchstaben "a", "b" oder "c".  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie dem regulären Ausdruck die rechte eckige Klammer hinzu.  
  
    > [!NOTE]
    > Wenn Sie eine einzelne eckige Klammer abgleichen möchten, versehen Sie Sie mit einem umgekehrten Schrägstrich \\[-damit Sie nicht als Sonderzeichen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]interpretiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekt für reguläre Ausdrücke](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)