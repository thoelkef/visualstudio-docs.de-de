---
title: Erwartet ') "im regulären Ausdruck (JavaScript) | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 7daf5d876f68168ce0b58ea2cc9b52a309107bc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446530"
---
# <a name="expected--in-regular-expression-javascript"></a>Im regulären Ausdruck wurde ')' erwartet (JavaScript)
Sie haben versucht, einem regulären Ausdruck erfassen, Assertion oder einer Gruppe zu erstellen, aber es hat keine die schließenden Klammer. Klammern haben mehrere Zwecke in regulären Ausdrücken. Sie werden in erster Linie verwendet, zum Erfassen von Unterausdrücken an Assertionen oder Muster gruppieren, sodass die Elemente behandelt werden können, als eine Einheit von *, +,?, und so weiter.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Fügen Sie der letzten schließenden Klammern hinzu.  
  
    > [!NOTE]
    > Sie können eine einzelne Klammer entsprechend mit Escapezeichen versehen sie mit einem umgekehrten Schrägstrich - \\(–, damit es nicht als Sonderzeichen von interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax für reguläre Ausdrücke (JavaScript)](https://msdn.microsoft.com/library/1400241x)