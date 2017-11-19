---
title: "Übersicht über das Sprache Protokoll | Microsoft Docs"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aeef820575a4fb055318fe11d401e85c9958bad
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="language-server-protocol"></a>Language-Server-Protokoll

## <a name="what-is-the-language-server-protocol"></a>Was ist das Serverprotokoll Sprache?

Unterstützende umfangreichen Bearbeitungsfunktionen wie Source Code Auto-Beendigungen oder **Gehe zu Definition** für ein Programmiersprache Ihrer Wahl in einem Editor oder IDE normalerweise sehr schwierig und zeitaufwendig ist. In der Regel muss es ein Domänenmodell (einen Scanner, ein Parser, einen Typ aus, einen Generator usw.) in der Programmiersprache des Editors oder IDE geschrieben werden sollen. Beispielsweise wird der KDTZE Eclipse-Plug-Ins, die Unterstützung für C/C++ in der Eclipse-IDE bietet in Java geschrieben, seit der Eclipse-IDE selbst in Java geschrieben ist. Nach dieser Ansatz würde dies bedeuten, implementieren ein C/C++-Domänenmodell in TypeScript für Visual Studio-Code und eine separate Domänenmodell in c# für Visual Studio.

Erstellen von sprachspezifischen Domänenmodelle sind auch viel einfacher, wenn ein Entwicklungstool vorhandene sprachspezifische Bibliotheken wiederverwenden kann. Diese Bibliotheken sind jedoch in der Regel implementiert, in der Programmiersprache selbst (z. B. gute C/C++-Domäne, die Modelle in C/C++-implementiert sind). Integrieren von einer C/C++-Bibliothek in einem Editor, geschrieben in TypeScript ist technisch möglich aber schwierig.

### <a name="language-servers"></a>Language-Servern

Ein anderer Ansatz ist die Bibliothek in einem eigenen Prozess ausgeführt, und verwenden prozessübergreifende Kommunikation zu sprechen. Die Nachrichten hin-und bilden ein Protokoll. Die Language-Serverprotokolls (LSPS) ist das Produkt der Standardisierung der zwischen ein Entwicklungstool und einem Serverprozess Sprache ausgetauschten Nachrichten. Mit Language-Servern oder wer's ist keine neuen oder Novel Idee. Editoren, z. B. Vim und Emacs dadurch für einige Zeit in semantische automatische Vervollständigung unterstützen Aktionen ausgeführt wurden. Das Ziel des LSP wurde vereinfacht diese Arten von Integrationen und ein nützlich-Framework zum Verfügbarmachen von Sprachfunktionen, um eine Vielzahl von Tools bereitgestellt.

Über ein gemeinsames Protokoll ermöglicht die Integration der Programmierung von Sprachfunktionen in ein Entwicklungstool mit minimalen selbst durchführt, wenn Sie eine vorhandene Implementierung von der Sprache Domänenmodell wiederverwenden. Eine Sprache-Server als Back-End in PHP, Python oder Java geschrieben werden konnte und LSP können sie problemlos in eine Vielzahl von Tools integriert werden. Das Protokoll arbeitet auf einer gemeinsamen Ebene der Abstraktion, sodass ein Tool umfangreiche Sprachdienste bieten kann, ohne spezifisch für die zugrunde liegenden Domänenmodell feinheiten vollständig zu verstehen.

## <a name="how-work-on-the-lsp-started"></a>Funktionsweise von auf LSP gestartet

LSP wurde mit der Zeit weiterentwickelt und heute sie befindet sich auf Version 3.0. Er gestartet, wenn das Konzept eines Servers für die Sprache von OmniSharp übernommen wurde, um umfangreiche Bearbeitungsfeatures für c# bieten. Zu Beginn OmniSharp verwendet das HTTP-Protokoll mit einem JSON-Nutzlast und wurde in mehreren Editoren einschließlich integriert [Visual Studio Code](https://code.visualstudio.com).

Ungefähr zur selben Zeit gestartet Microsoft arbeiten auf einem Server TypeScript-Sprache, mit der Idee TypeScript in Editoren, z. B. Emacs und Sublime Text zu unterstützen. In dieser Implementierung ein Editors kommuniziert über dem Stdin / "stdout", bei denen die TypeScript-Serverprozess und eine JSON-Nutzlast, die vom Debugger Protokoll V8 Inspiration für Anforderungen und-Antworten verwendet. Die TypeScript-Server wurde in die Sublime TypeScript-Plug-in und Visual Studio Code zum Bearbeiten von umfangreichen TypeScript integriert.

Gestartet wurde in integrierten zwei unterschiedliche Sprachen Server haben, das Visual Studio Code-Team ein common Language-Server-Netzwerkprotokoll für Editoren und IDEs zu untersuchen. Ein häufig verwendetes Protokoll ermöglicht einen Sprachanbieter einsprachige Server zu erstellen, der von anderen IDEs genutzt werden können. Ein Server-Consumer Sprache muss nur einmal implementiert die Clientseite des Protokolls. Dadurch wird eine Win-Win-Situation für das Language-Anbieter und der Consumer Sprache.

Mit dem Language-Protokoll verwendet, die vom Server TypeScript gestartet, war es mehrere allgemeine und sprachneutral. Das Protokoll wurde mit mehr mithilfe von Visual Studio Code-Sprachen-API für Inspiration Sprachfunktionen. Das Protokoll selbst wird mit JSON-RPC für remote-Aufruf aufgrund seiner Einfachheit und Support-Bibliotheken für viele Programmiersprachen unterstützt.

Visual Studio Code Team Dogfooded des Protokolls durch die Implementierung von mehreren Linter Language-Servern. Ein Linter Sprache Server reagiert auf Anforderungen an fusselfreien (Überprüfung) eine Datei und gibt eine Menge von erkannte Warnungen und Fehler. Das Ziel war fusselfreien einer Datei als die benutzerbearbeitungen in einem Dokument, das bedeutet, dass sich viele Linting Anforderungen während einer editorsitzung für. Es sinnvoll, zu einem Server einrichten und ausführen, damit ein neuer Prozess für die Linting muss nicht für jeden Benutzer bearbeiten gestartet werden. Mehrere Linter Server implementiert wurden, einschließlich Visual Studio-Code ESLint und TSLint-Erweiterungen. Dieser beiden Linter Server werden sowohl in TypeScript/JavaScript implementiert und auf Node.js ausgeführt. Beide weisen eine Bibliothek, die die Client-als auch Teil des Protokolls implementiert.

## <a name="how-the-lsp-works"></a>Wie funktioniert die LSP

Ein Sprache-Server in einem eigenen Prozess ausgeführt wird, und Tools wie Visual Studio oder Visual Studio Code mit dem Server mithilfe des Language-Protokolls über JSON-RPC-Kommunikation. Ein weiterer Vorteil von der Sprache des Serverbetriebssystems in einem dedizierten Prozess ist, dass das Leistungsproblemen im Zusammenhang mit einem einzelnen Prozessmodell vermieden werden. Der tatsächliche Transportkanal kann entweder sein, Stdio, Sockets, named Pipes oder Knoten Ipc Wenn Client und Server in Node.js geschrieben werden.

Im folgenden ist ein Beispiel für die Kommunikation zwischen der ein Tool und eine Sprache-Server während einer Routine Sitzung bearbeiten:

![LSP-Flussdiagramm](media/lsp-flow-diagram.png)

* **Der Benutzer öffnet eine Datei (bezeichnet als ein Dokument) im Tool**: benachrichtigt dem Language-Server, dass ein Dokument geöffnet ist ("TextDocument/DidOpen"). Von nun an die Wahrheit über den Inhalt des Dokuments nicht mehr im Dateisystem wird jedoch vom Tool im Arbeitsspeicher beibehalten.

* **Der Benutzer stellt Bearbeitungen**: das Tool informiert des Servers über die Änderung des Dokuments ("TextDocument/DidChange"), und die semantische Informationen des Programms durch die Language-Server aktualisiert wird. Wie in diesem Fall wird die Sprache Server Ebenenlaufzeitsystem analysiert, und diese Informationen und benachrichtigt das Tool mit der erkannten Fehler und Warnungen ("TextDocument/PublishDiagnostics").

* **Der Benutzer führt "Gehe zu Definition" auf ein Symbol im Editor**: das Tool sendet eine Anforderung "TextDocument/Definition" mit zwei Parametern: (1) das Dokument URI und (2) die Position aus, in dem die Gehe zu Definition-Anforderung an den Server initiiert wurde. Der Server antwortet mit dem Dokument URI und die Position des Symboldefinition innerhalb des Dokuments.

* **Der Benutzer schließt das Dokument (Datei)**: "TextDocument/DidClose" Benachrichtigung wird gesendet, aus dem Tool, das Language-Server, der das Dokument ist nun nicht mehr im Arbeitsspeicher und die, die den aktuellen Inhalt ist jetzt im Dateisystem auf dem neuesten Stand zu informieren.

In diesem Beispiel wird veranschaulicht, wie das Protokoll mit dem Language-Server auf der Ebene der Editorfunktionen wie "Gehe zu Definition", "Alle Verweise suchen" kommuniziert. Die Datentypen, die vom Protokoll verwendete sind Editor oder IDE "Datentypen", wie der aktuell geöffneten Text-Dokument und die Position des Cursors. Die Datentypen sind nicht auf der Ebene der ein programming Language Domänenmodell die abstrakte Syntaxstrukturen und Compiler-Symbole (z. B. aufgelösten Typen, Namespaces,...) in der Regel bereitstellen möchten. Dadurch wird das Protokoll erheblich vereinfacht.

Jetzt sehen wir uns die Anforderung ' TextDocument/Definition' im Detail. Im folgenden sind die Nutzlasten, die zwischen dem Clienttool und die Language-Server für die Anforderung "Gehe zu Definition" in einem C++-Dokument.

Die Anforderung sieht folgendermaßen aus:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Dies ist die Antwort aus:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Rückblickend ist, beschreibt die Datentypen, die auf der Ebene des Editors statt auf der Ebene des Programmiermodells Sprache eine der Gründe für den Erfolg des Language-Server-Netzwerkprotokolls. Es ist viel einfacher, ein Textdokument URI zu standardisieren, oder die Cursorposition im Vergleich mit standardisieren ein abstract Syntax Tree und Compiler-Symbolen in verschiedenen Programmiersprachen.

Wenn ein Benutzer mit verschiedenen Sprachen arbeitet, startet VS-Code in der Regel einen Sprache-Server für jede Programmiersprache. Das folgende Beispiel zeigt eine Sitzung, in dem der Benutzer Java-und SASS arbeitet.

![Java und sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funktionen

Nicht jeder Sprache-Server kann alle Funktionen, die definiert, die vom Protokoll unterstützen. Client und Server kündigt daher ihre unterstützten Funktionsumfang durch "Funktionen" auf. Beispielsweise können kündigt ein Server, kann er die Anforderung ' TextDocument/Definition' verarbeiten, aber die "Arbeitsbereich/Symbol" Anforderung nicht behandeln kann. Auf ähnliche Weise können Clients bekannt, dass sie "zum Speichern" bereitstellen können Benachrichtigungen auf, bevor ein Dokument gespeichert wird, sodass Text bearbeitet, um automatisch die bearbeitete Dokument formatieren von ein Server verarbeitet werden kann.

## <a name="integrating-a-language-server"></a>Integrieren von einer Sprache-server

Die eigentliche Integration eines Servers Sprache in ein bestimmtes Tool wird nicht durch das Serverprotokoll Sprache definiert und an das Tool in einer Implementierung bleibt. Einige Tools integrieren Sprache Servern generisch, da eine Erweiterung, die gestartet und für jede Art von Sprache-Server kommunizieren kann. Andere erstellen wie Visual Studio-Code, eine benutzerdefinierte Erweiterung pro Sprache-Server, damit eine Erweiterung noch einige benutzerdefinierte Sprachfunktionen bereitstellen kann.

Um die Implementierung von Sprache-Servern und Clients zu vereinfachen, Bibliotheken oder vorliegen SDKs für die Client- und Teile. Diese Bibliotheken sind für verschiedene Sprachen bereitgestellt. Es ist z. B. eine [Client Npm-Sprachmodul](https://www.npmjs.com/package/vscode-languageclient) zum Vereinfachen der Integration von einer Sprache-Server in einer Visual Studio Code-Erweiterung und ein anderes [Server Npm-Sprachmodul](https://www.npmjs.com/package/vscode-languageserver) , einen Language-Server, die mit Node.js zu schreiben. Dies ist die aktuelle [Liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) Support-Bibliotheken.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Verwenden das Serverprotokoll Sprache in Visual Studio

* [Hinzufügen einer Erweiterung der Sprache Serverprotokoll](adding-an-lsp-extension.md) -erfahren Sie mehr über einen Server für die Sprache in Visual Studio integrieren.
