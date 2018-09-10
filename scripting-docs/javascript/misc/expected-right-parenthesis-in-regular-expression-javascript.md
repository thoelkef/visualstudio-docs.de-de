---
title: Erwartet &#39;)&#39; im regulären Ausdruck (JavaScript) | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279127"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Erwartet &#39;)&#39; im regulären Ausdruck (JavaScript)
Sie haben versucht, einem regulären Ausdruck erfassen, Assertion oder einer Gruppe zu erstellen, aber es hat keine die schließenden Klammer. Klammern haben mehrere Zwecke in regulären Ausdrücken. Sie werden in erster Linie verwendet, zum Erfassen von Unterausdrücken an Assertionen oder Muster gruppieren, sodass die Elemente behandelt werden können, als eine Einheit von *, +,?, und so weiter.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie der letzten schließenden Klammern hinzu.  
  
    > [!NOTE]
    >  Sie können eine einzelne Klammer entsprechend mit Escapezeichen versehen sie mit einem umgekehrten Schrägstrich - \\(–, damit es nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)