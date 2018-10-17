---
title: Erwartet &#39;]&#39; im regulären Ausdruck (JavaScript) | Microsoft-Dokumentation
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
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283716"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Erwartet &#39;]&#39; im regulären Ausdruck (JavaScript)
Sie haben versucht, eine Zeichenklasse für die Übereinstimmung eines regulären Ausdrucks zu erstellen, aber Sie hat keine die schließenden Klammer. Einzelne Literalzeichen Kombinationen können zu Zeichenklassen in regulären Ausdrücken zusammengefügt werden, Ausschnitte in Klammern aufgerufen wird. Eine Zeichenklasse entspricht einem beliebigen Zeichen, die, das Sie enthält. Z. B. / [Abc] / entspricht einem beliebigen Buchstaben "a", "b" oder "c".  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie der schließenden Klammer des regulären Ausdrucks ein.  
  
    > [!NOTE]
    >  Sie können eine einzelne Klammer entsprechend mit Escapezeichen versehen sie mit einem umgekehrten Schrägstrich - \\[–, damit es nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)