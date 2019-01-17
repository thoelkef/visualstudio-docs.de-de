---
title: Erwartet ']' im regulären Ausdruck (JavaScript) | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0b34ae4bdf04d261647b9096cda13eec75617c5
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349425"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ']' erwartet (JavaScript)
Sie haben versucht, eine Zeichenklasse für die Übereinstimmung eines regulären Ausdrucks zu erstellen, aber Sie hat keine die schließenden Klammer. Einzelne Literalzeichen Kombinationen können zu Zeichenklassen in regulären Ausdrücken zusammengefügt werden, Ausschnitte in Klammern aufgerufen wird. Eine Zeichenklasse entspricht einem beliebigen Zeichen, die, das Sie enthält. Z. B. / [Abc] / entspricht einem beliebigen Buchstaben "a", "b" oder "c".  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie der schließenden Klammer des regulären Ausdrucks ein.  
  
    > [!NOTE]
    >  Sie können eine einzelne Klammer entsprechend mit Escapezeichen versehen sie mit einem umgekehrten Schrägstrich - \\[–, damit es nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)