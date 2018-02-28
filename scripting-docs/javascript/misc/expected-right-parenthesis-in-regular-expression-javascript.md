---
title: "Erwartete &#39;) &#39; im regulären Ausdruck (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Erwartete &#39;) &#39; im regulären Ausdruck (JavaScript)
Sie hat versucht, einen regulären Ausdruck erfasst, die Assertion oder die Gruppe zu erstellen, jedoch keine die schließenden Klammer. Klammern haben mehrere Zwecke in regulären Ausdrücken. Sie werden in erster Linie verwendet, um das Erfassen der Teilausdrücke, Angeben von Assertionen oder Muster gruppieren, sodass die Elemente als einzelne Einheit von behandelt werden können *, +,?, und so weiter.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Fügen Sie der letzten schließenden Klammern hinzu.  
  
    > [!NOTE]
    >  Wenn Sie eine einzelne Klammer anpassen möchten, mit Escapezeichen versehen sie mit einem umgekehrten Schrägstrich - \\(–, damit er nicht als Sonderzeichen durch interpretiert wird [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)