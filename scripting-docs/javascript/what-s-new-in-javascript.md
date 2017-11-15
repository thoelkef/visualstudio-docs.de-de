---
title: Neues in JavaScript | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="what39s-new-in-javascript"></a>Neues in JavaScript
In diesem Dokument werden neue Funktionen von JavaScript aufgeführt, die sowohl im [Edgemodus](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] als auch in Windows Phone Store-Apps unterstützt werden.  
  
 Informationen zu JavaScript-Elementen, die im Edgemodus unterstützt werden, jedoch in [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)]-Apps veraltet sind, finden Sie unter [Versionsinformationen](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Informationen zur Erstellung von [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] und Windows Phone Store-Apps, die mit JavaScript für Windows erstellt werden, einschließlich Informationen über den Visual Studio-JavaScript-Editor und andere Funktionen, finden Sie unter [Entwickeln von Windows Store-Apps mit Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Neue Funktionen in JavaScript  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Klassen|Neue Syntax unterstützt die Deklaration von [Klassen](../javascript/reference/class-statement-javascript.md).|  
|Promises|[Promises](../javascript/reference/promise-object-javascript.md) ermöglichen eine leichtere und sauberere asynchrone Codierung. Promise-Konstruktoren werden unterstützt, zusammen mit den Hilfsmethoden `all` und `race`.|  
|Iteratoren|Jetzt können Sie iterierbare Objekte (einschließlich Arrays, arrayähnliche Objekte und Iteratoren) wiederholt durchlaufen und dabei einen benutzerdefinierten Iterationshaken mit Anweisungen aufrufen, die für den Wert jeder einzelnen Eigenschaft ausgeführt werden sollen. Weitere Informationen finden Sie unter [Iteratoren und Generatoren](../javascript/advanced/iterators-and-generators-javascript.md). **Hinweis:** Generatoren werden noch nicht unterstützt.|  
|Pfeilfunktionen|Die Pfeilfunktion (= >) bietet eine Kurzsyntax für das Schlüsselwort `function`, dass eine lexikalische `this`-Bindung darstellt.|  
|Neue Methoden für integrierte Objekte|Die integrierten Objekte [Array-Objekt](../javascript/reference/array-object-javascript.md), [Math-Objekt](../javascript/reference/math-object-javascript.md), [Number-Objekt](../javascript/reference/number-object-javascript.md), [Object-Objekt](../javascript/reference/object-object-javascript.md) und [String-Objekt](../javascript/reference/string-object-javascript.md) umfassen viele neue Hilfsfunktionen und Eigenschaften zum Bearbeiten und Überprüfen von Daten.|  
|Verbesserungen des Objektliterals|Objekte unterstützen nun berechnete Eigenschaften, präzise Methodendefinitionen und eine Kurzsyntax für Eigenschaften, deren Wert für eine gleichnamige Variable initialisiert wird. Weitere Informationen finden Sie unter [Erstellen von Objekten](../javascript/creating-objects-javascript.md).|  
|Proxys|[Proxys](../javascript/reference/proxy-object-javascript.md) ermöglichen ein benutzerdefiniertes Verhalten für Objekte.|  
|Rest-Parameter|Mit Rest-Parametern können Sie aufeinanderfolgende Argumente in einem Funktionsaufruf in einen Array umwandeln. Weitere Informationen finden Sie unter [Funktionen](../javascript/functions-javascript.md).|  
|Spread-Operator|Der [Spread-Operator](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) erweitert iterierbare Ausdrücke in einzelne Argumente. Beispielsweise entspricht `a.b(...array)` ungefähr `a.b.apply(a, array)`.|  
|Symbole|Mit [Symbol](../javascript/reference/symbol-object-javascript.md)-Objekten können Eigenschaften vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.|  
|Vorlagenzeichenfolgen|[Vorlagenzeichenfolgen](../javascript/advanced/template-strings-javascript.md) sind Zeichenfolgenliterale, mit denen Ausdrücke ausgewertet und mit dem Zeichenfolgenliteral verkettet werden können.|  
|Unicode-Verbesserungen|Es wurden Verbesserungen der Unicode-Unterstützung vorgenommen. Beispielsweise unterstützt ein neues Escapesequenzformat astrale Codepunkte (Codepunkte mit mehr als vier Hexadezimalziffern). Weitere Informationen finden Sie unter [Sonderzeichen](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|Ein [WeakSet](../javascript/reference/weakset-object-javascript.md) ist eine Auflistung von Objekten, für die eine Garbage Collection durchgeführt wird, wenn nicht an anderer Stelle auf sie verwiesen wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Sprachreferenz](../javascript/javascript-language-reference.md)