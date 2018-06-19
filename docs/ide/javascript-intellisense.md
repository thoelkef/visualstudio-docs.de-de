---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16e0efd8393d6324321a505247a3dad171a81a57
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103475"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] bietet eine leistungsfähige direkte JavaScript-Zuordnung. Unterstützt von einem TypeScript-basierten Sprachdienst, bietet Visual Studio umfangreichere IntelliSense, Support für moderne JavaScript-Funktionen und verbesserte Produktivitätsfeatures wie die „Gehe zu Definition“, die Umgestaltung und vieles mehr.

> [!NOTE]
> Der JavaScript-Sprachdienst in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] verwendet eine neue Engine für den Sprachdienst mit dem Namen „Salsa“. Details dazu finden Sie in diesem Artikel und im folgenden [Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc). Der neue Bearbeitungsvorgang gilt weitestgehend auch für Visual Studio Code. Finden Sie unter [VS Code docs (VS Code Dokumentation)](https://code.visualstudio.com/docs/languages/javascript) weitere Informationen.

Weitere Informationen zur allgemeinen IntelliSense-Funktionalität von Visual Studio finden Sie unter [Using IntelliSense (Verwenden von IntelliSense)](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Neues im JavaScript-Sprachdienst in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Ab [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] zeigt JavaScript IntelliSense eine Vielzahl weiterer Informationen zu Parameter- und Memberlisten an.
Diese neuen Informationen werden vom TypeScript-Sprachdienst bereitgestellt, der statische Analyse im Hintergrund verwendet, um Ihren Code besser zu verstehen.
TypeScript verwendet mehrere Quellen, um diese Informationen zu erstellen:

- [IntelliSense basierend auf dem Typrückschluss](#TypeInference)
- [IntelliSense basierend auf JSDoc](#JsDoc)
- [IntelliSense based on TypeScript declaration files (IntelliSense basierend auf TypeScript-Deklarationsdateien)](#TsDeclFiles)
- [Automatische Übernahme von Typdefinitionen](#Auto)

<a name="TypeInference"></a>
### <a name="intellisense-based-on-type-inference"></a>IntelliSense (auf Typrückschluss basierend)

In JavaScript ist in den meisten Fällen keine explizite Typinformationen verfügbar. Glücklicherweise ist es in der Regel recht einfach, einen Typ mit dem angegebenen umgebenden Codekontext abzuleiten.
Dieser Prozess wird als Typrückschluss bezeichnet.

Für eine Variable oder eine Eigenschaft ist der Typ in der Regel der Typ des Werts, der verwendet wird, um sie oder die aktuelle Zuweisung von Werten zu initialisieren.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Für eine Funktion kann der Rückgabetyp von den return-Anweisungen hergeleitet werden.

Für die Funktionsparameter ist derzeit kein Rückschluss vorhanden, aber es gibt Möglichkeiten, dieses Problem mithilfe von *D.TS*-Dateien von JSDoc oder TypeScript (siehe weiter unten) zu umgehen.

Darüber hinaus gibt es spezielle Rückschlüsse für Folgendes:

- „ES3-Style“-Klassen, die mit einer Konstruktorfunktion und Zuweisungen der prototype-Eigenschaft angegeben sind.
- CommonJS-Stil Modul Muster, die als Eigenschaftenzuweisungen auf das `exports`-Objekt oder Zuweisungen zu der `module.exports`-Eigenschaft angegeben sind.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>
### <a name="intellisense-based-on-jsdoc"></a>IntelliSense (auf JSDoc basierend)

Wo der Typrückschluss nicht die gewünschten Typinformationen bietet (oder die Dokumentation unterstützt), können Typinformationen ausdrücklich über JSDoc-Anmerkungen angegeben werden.  Sie können beispielsweise den `@type`-Tag wie im Folgenden verwenden, um einem teilweise deklarierten Objekt einen bestimmten Typ zu geben:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Wie bereits erwähnt, werden Funktionsparameter nie hergeleitet. Verwenden Sie jedoch den JSDoc `@param`-Tag, können Sie auch Typen zu Funktionsparametern hinzufügen.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Weitere Informationen zu den derzeit unterstützten JSDoc-Anmerkungen finden Sie unter [JSDoc support in JavaScript (JSDoc-Unterstützung in JavaScript)](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript).

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense (auf TypeScript-Deklarationsdateien basierend)

Da JavaScript und TypeScript jetzt auf dem gleichen Sprachdienst basieren, können sie auf umfangreichere Weise interagieren. Beispielsweise kann JavaScript IntelliSense für die deklarierten Werte in der *D.TS*-Datei bereitgestellt werden (Weitere Infos), und in TypeScript deklarierte Typen wie Schnittstellen und Klassen stehen für die Verwendung als Typen in JSDoc-Kommentaren zur Verfügung. Weitere Informationen finden Sie in der [Dokumentation zu TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

Im Folgenden wird ein einfaches Beispiel für eine TypeScript-Definitionsdatei dargestellt, die solche Typinformationen (über eine Schnittstelle) in einer JavaScript-Datei im selben Projekt (mit einem `JsDoc`-Tag) bereitstellt.

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640" alt="TypeScript definition file" />

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatische Übernahme von Typdefinitionen

In TypeScript werden die APIs der am häufigsten verwendeten JavaScript-Bibliotheken durch *D.TS*-Dateien beschrieben, und die am häufigsten verwendete Repository für diese Definitionen befindet sich unter [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Standardmäßig versucht der Sprachdienst Salsa zu ermitteln, welche JavaScript-Bibliotheken verwendet werden. Er lädt die entsprechende *D.TS*-Datei automatisch herunter, die die Bibliothek beschreibt, und verweist darauf, um IntelliSense umfangreicher bereitzustellen. Die Dateien werden in einen Cache, der sich im Benutzerordner unter *%LOCALAPPDATA%\Microsoft\TypeScript* befindet, heruntergeladen.

> [!NOTE]
> Dieses Feature ist standardmäßig **deaktiviert**, wenn eine *TSCONFIG.JSON*-Konfigurationsdatei verwendet wird, kann jedoch wie im Folgenden beschrieben auf „aktiviert“ festgelegt werden.

Die automatische Erkennung funktioniert derzeit für Abhängigkeiten, die von npm (durch Lesen der *PACKAGE.JSON*-Datei) oder Bower (durch Lesen der *BOWER.JSON*-Datei) heruntergeladen werden, sowie für lose Dateien im Projekt, die mit einer Liste übereinstimmen, die ungefähr die 400 beliebtesten JavaScript-Bibliotheken enthält. Wenn beispielsweise *jquery-1.10.min.js* in Ihrem Projekt vorhanden ist, wird die Datei *jquery.d.ts* abgerufen und geladen, um eine bessere Bearbeitung zu ermöglichen. Diese *D.TS*-Datei hat keine Auswirkung auf Ihr Projekt.

Wenn Sie die automatische Übernahme nicht verwenden möchten, deaktivieren Sie sie durch das Hinzufügen einer Konfigurationsdatei, wie unten beschrieben. Sie können immer noch manuell Definitionsdateien für die Verwendung direkt in Ihrem Projekt hinzufügen.

## <a name="see-also"></a>Siehe auch

- [Verwenden von IntelliSense](../ide/using-intellisense.md)