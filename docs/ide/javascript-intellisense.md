---
title: JavaScript IntelliSense | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] bietet eine leistungsfähige direkte JavaScript-Zuordnung. Unterstützt von einem TypeScript-basierten Sprachdienst, bietet Visual Studio umfangreichere IntelliSense, Support für moderne JavaScript-Funktionen und verbesserte Produktivitätsfeatures wie die „Gehe zu Definition“, die Umgestaltung und vieles mehr.

> [!NOTE]
>  Der JavaScript-Sprachdienst in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] verwendet ein neues Modul für den Sprachdienst („Salsa“). Details sind hier in diesem Thema enthalten. Möglicherweise möchten Sie auch diesen [Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/) lesen. Die neue Zuordnung gilt meistens auch im VS Code. Finden Sie unter [VS Code docs (VS Code Dokumentation)](https://code.visualstudio.com/docs/languages/javascript) weitere Informationen.

Weitere Informationen zur allgemeinen IntelliSense-Funktionalität von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Neues im JavaScript-Sprachdienst in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- Umfangreichere IntelliSense

    JavaScript IntelliSense in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] zeigt jetzt eine Vielzahl weiterer Informationen für Parameter- und Memberlisten an.
Diese neuen Informationen werden vom TypeScript-Sprachdienst bereitgestellt, der statische Analyse im Hintergrund verwendet, um Ihren Code besser zu verstehen.
TypeScript verwendet mehrere Quellen, um diese Informationen zu erstellen.
    - [IntelliSense basierend auf dem Typrückschluss](#TypeInference)
    - [IntelliSense basierend auf JSDoc](#JsDoc)
    - [IntelliSense basierend auf TypeScript Deklarationsdateien](#TSDeclFiles)

- [Automatische Übernahme von Typdefinitionen](#Auto)
- [Support für ES6 und darüber hinaus](#ES6)
- [Support für JSX-Syntax](#JSX)

## <a name="TypeInference"></a>IntelliSense basierend auf den Typrückschluss
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

Für die Funktionsparameter ist derzeit kein Rückschluss vorhanden, aber es gibt Möglichkeiten, dieses Problem mithilfe von JSDoc oder TypeScript `.d.ts`-Dateien (siehe weiter unten) zu umgehen.

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

## <a name="JsDoc"></a> IntelliSense basierend auf JSDoc

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
 
Weitere Informationen finden Sie unter [diesem Dokument](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) für JsDoc-Anmerkungen, die derzeit unterstützt werden.

## <a name="TsDeclFiles"></a> IntelliSense basierend auf TypeScript Deklarationsdateien

Da JavaScript und TypeScript jetzt auf dem gleichen Sprachdienst basieren, können sie auf umfangreichere Weise interagieren. Beispielsweise kann JavaScript IntelliSense für die deklarierten Werte in der `.d.ts`-Datei bereitgestellt werden ([Weitere Infos](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)), und in TypeScript deklarierte Typen wie Schnittstellen und Klassen stehen für die Verwendung als Typen in JsDoc-Kommentaren zur Verfügung. 

Im folgenden zeigen wir ein einfaches Beispiel für eine TypeScript-Definitionsdatei, die solche Typinformationen (über eine Schnittstelle) in eine JavaScript-Datei im selben Projekt (mit einem JsDoc-Tag) bereitstellt.

_**TypeScript-Deklarationen, die in JavaScript verwendet werden**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Automatische Übernahme von Typdefinitionen
In der TypeScript-Welt lassen die am häufigsten verwendeten JavaScript-Bibliotheken ihre APIs durch `.d.ts`-Dateien beschreiben, und die am häufigsten verwendete Repository für diese Definitionen befindet sich auf [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Standardmäßig versucht der Sprachdienst Salsa zu ermitteln, welche JavaScript-Bibliotheken verwendet werden. Er lädt die entsprechende `.d.ts`-Datei, die die Bibliothek beschreibt, um umfangreichere IntelliSense bereitzustellen, automatisch herunter und verweist darauf. Die Dateien werden auf einen Cache, der sich unter dem Benutzerordner auf `%LOCALAPPDATA%\Microsoft\TypeScript` befindet, heruntergeladen. 

> [!NOTE]
> Dieses Feature ist standardmäßig **deaktiviert**, wenn eine `tsconfig.json`-Konfigurationsdatei verwendet wird, aber kann wie weiter unten beschrieben auf „aktiviert“ festgelegt werden.

Die automatische Erkennung arbeitet derzeit für Abhängigkeiten, die von npm heruntergeladen werden (durch Lesen der `package.json`-Datei), Bower (durch Lesen der `bower.json`-Datei), und für lose Dateien im Projekt, die einer Liste mit den ungefähr 400 beliebtesten JavaScript-Bibliotheken entsprechen. Angenommen Sie haben `jquery-1.10.min.js` in Ihrem Projekt, dann wird die Datei `jquery.d.ts` abgerufen und geladen, um eine bessere Zuordnung zu bieten. Diese `.d.ts`-Datei hat keine Auswirkung auf Ihr Projekt. 

Wenn Sie die automatische Übernahme nicht verwenden möchten, deaktivieren Sie sie durch das Hinzufügen einer Konfigurationsdatei, wie unten beschrieben. Sie können immer noch manuell Definitionsdateien für die Verwendung direkt in Ihrem Projekt hinzufügen.

## <a name="ES6"></a> Support für ES6 und darüber hinaus

ES6 oder ECMAScript 2015 ist die nächste Version von JavaScript. Dadurch erhält die Programmiersprache neue Syntax, z.B. Klassen, Pfeilfunktionen, `let`/`const`, und vieles mehr. Die neue Syntax wird in Visual Studio unterstützt.

Eine der wichtigsten Features, die TypeScript bietet, ist die Möglichkeit, ES6-Funktionen zu verwenden, und Code auszugeben, der in JavaScript-Laufzeiten ausgeführt werden kann, die noch nicht die neueren Funktionen verstehen. Dies wird häufig als „Transpilierung“ bezeichnet. Da JavaScript den gleichen Sprachdienst verwendet, kann es auch Vorteile aus der ES6+ bis ES5-Transpilation ziehen.

Bevor dies eingerichtet werden kann, ist ein Verständnis für die Konfigurationsoptionen erforderlich.  TypeScript ist über eine `tsconfig.json`-Datei konfiguriert. Wenn eine solche Datei nicht vorhanden ist, werden einige Standardwerte verwendet. Aus Gründen der Kompatibilität unterscheiden sind diese Standards in einem Kontext, in dem nur JavaScript-Dateien (und optional `.d.ts`-Dateien) vorhanden sind. Um JavaScript-Dateien zu kompilieren, muss eine `tsconfig.json`-Datei hinzugefügt werden, und einige Standardeinstellungen müssen dann explizit festgelegt werden.

Die erforderlichen Einstellungen für die tsconfig-Datei werden im Folgenden beschrieben:

 - `allowJs`: Dieser Wert muss auf `true` festgelegt werden, damit JavaScript-Dateien erkannt werden.
Standardmäßig ist dies `false`, da TypeScript in JavaScript kompiliert wird, und dies ist erforderlich, um zu vermeiden, dass der Compiler Dateien enthält, die gerade kompiliert wurden.
 - `outDir`: Dies sollte an einem Speicherort festgelegt werden, der nicht im Projekt enthalten ist, damit die ausgegebenen JavaScript-Dateien nicht erkannt und anschließend in das Projekt einbezogen werden (siehe `exclude` unten).
 - `module`: Wenn Sie Module verwenden, weist diese Einstellung den Compiler an, welches Modulformat der ausgegebene Code verwenden sollte (z.B. `commonjs` für Knoten oder Bundler wie Browserify).
 - `exclude`: Diese Einstellung gibt die Ordner an, die nicht im Projekt eingeschlossen werden sollen. 
 Sowohl der Ausgabeort als auch Ordner, die nicht Teil des Projekts sind, wie z.B. `node_modules` oder `temp`, sollten zu dieser Einstellung hinzugefügt werden.
 - `enableAutoDiscovery`: Diese Einstellung ermöglicht die automatische Erkennung und das Herunterladen von Definitionsdateien, wie oben beschrieben.
 - `compileOnSave`: Diese Einstellung weist den Compiler an, ob er jederzeit neu kompilieren soll, wenn eine Quelldatei in Visual Studio gespeichert ist.

Um JavaScript-Dateien in CommonJS-Modulen in einen `./out`-Ordner zu konvertieren, müssen möglicherweise Einstellungen in einer `tsconfig.json`-Datei enthalten sein, ähnlich wie die unten.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

Mit den obigen Einstellungen an einem Standort, wenn eine Quelldatei (`./app.js`) vorhanden ist, die mehrere ECMAScript 2015-Sprachfunktionen wie unten dargestellt enthält:

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Dann würde eine Datei zu `./out/app.js` ausgegeben werden, mit ECMAScript 5 (Standard) als Ziel, die etwa so aussieht wie unten:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Support für JSX-Syntax

JavaScript in Visual Studio 2017 bietet einen umfangreichen Support für die JSX-Syntax. JSX ist ein Syntaxset, das HTML-Tags in JavaScript-Dateien erlaubt. 

Die folgende Abbildung zeigt eine react-Komponente, die in der `comps.tsx`-TypeScript-Datei definiert ist, und anschließend wird diese Komponente von der `app.jsx`-Datei verwendet, die mit IntelliSense für Abschlüsse und Dokumentation in die JSX-Ausdrücke ausgeführt wird.
Sie brauchen hier kein TypeScript, dieses spezielle Beispiel enthält hier nur auch einige TypeScript-Codes.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Für die Konvertierung der JSX-Syntax in React-Aufrufe, muss die Einstellung `"jsx": "react"` in `compilerOptions` in der `tsconfig.json`-Datei hinzugefügt werden, wie oben beschrieben.

Der JavaScript-Datei, die in `./out/app.js' beim Build erstellt wird, würde diesen Code enthalten:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

