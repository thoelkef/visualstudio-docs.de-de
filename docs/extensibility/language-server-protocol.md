---
title: Übersicht über die Language-Server-Protokoll | Microsoft-Dokumentation
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b2329b54ba90a37e0d6d5e782e66c4af923a646
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828224"
---
# <a name="language-server-protocol"></a>Sprachserverprotokoll

## <a name="what-is-the-language-server-protocol"></a>Was ist das Sprachserverprotokoll?

Unterstützende umfangreichen Bearbeitungsfunktionen wie Quelle automatische codevervollständigung oder **Gehe zu Definition** für eine Programmiersprache in einem Editor oder die IDE normalerweise sehr schwierig und zeitaufwändig ist. In der Regel ist es erforderlich, schreiben ein Domänenmodell (einen Scanner, einen Parser, einen Typ aus, einen Generator usw.) in der Programmiersprache des Editors oder IDE. Beispielsweise ist das Plug-In für Eclipse KDTZE, bietet Unterstützung für C/C++ in der Eclipse-IDE in Java geschrieben, da der Eclipse-IDE selbst in Java geschrieben ist. Nach diesem Ansatz würde dies bedeuten, implementieren ein C-/C++-Domänenmodell in TypeScript für Visual Studio Code, und ein separates Domänenmodell in c# für Visual Studio.

Erstellen sprachspezifische Domänenmodelle sind auch viel einfacher, wenn ein Entwicklungstool für vorhandene sprachspezifische Bibliotheken wiederverwendet werden kann. Diese Bibliotheken sind jedoch in der Regel implementiert, in der Programmiersprache selbst (z. B. gute C/C++-Domäne, die in C/C++-Implementierung sind). Die Integration von einer C/C++-Bibliothek in einem Editor in TypeScript geschrieben ist technisch möglich, aber schwierig.

### <a name="language-servers"></a>Language-Server

Ein anderer Ansatz ist die Bibliothek in einem eigenen Prozess ausgeführt und prozessübergreifende Kommunikation, Kommunikation verwenden. Die Nachrichten hin-und bilden ein Protokoll. Das sprachserverprotokoll (LSP) ist das Produkt der Standardisierung von Nachrichten zwischen ein Entwicklungstool und einen Vorgang zur Sprache Server ausgetauscht werden. Mithilfe von Sprache-Servern oder wer's ist keine neue oder neuartige Idee. Editoren wie Vim und Emacs haben wurde dadurch für einige Zeit in semantische automatische Vervollständigung zu unterstützen. Das Ziel der LSP war, vereinfachen diese Arten von Integrationen und ein Framework nützlich für das Verfügbarmachen von Sprachfunktionen, um eine Vielzahl von Tools.

Mit einem gemeinsamen Protokoll ermöglicht die Integration von Sprachfeatures in ein Entwicklungstool, mit minimalen anfällt programmieren, indem Sie eine vorhandene Implementierung von der Sprache Domänenmodell wiederverwenden. Ein Language-Server als Back-End konnten in PHP, Python oder Java geschrieben werden, und LSP können sie ganz einfach in eine Vielzahl von Tools integriert werden. Das Protokoll funktioniert auf einer gemeinsamen Ebene der Abstraktion, damit ein Tool umfangreiche Sprachdienste bieten kann, ohne die Details in Bezug auf die zugrunde liegenden Domänenmodells für vollständig zu verstehen.

## <a name="how-work-on-the-lsp-started"></a>Wie funktionieren auf die Schritte gehen

LSP hat sich im Laufe der Zeit entwickelt, und heute ist er auf Version 3.0. Er gestartet, wenn das Konzept eines Servers für die Sprache von OmniSharp übernommen wurde, um umfassende Bearbeitungsfunktionen für C#-Code bereitzustellen. Zunächst OmniSharp verwendet das HTTP-Protokoll mit einem JSON-Nutzlast und wurde in verschiedene Editoren einschließlich integriert [Visual Studio Code](https://code.visualstudio.com).

Etwa zur gleichen Zeit gestartet Microsoft auf einem Server für das TypeScript-Sprache, mit dem Überblick über die Unterstützung von TypeScript in Editor wie Emacs und Sublime Text arbeiten. In dieser Implementierung ein Editors kommuniziert über "Stdin/stdout" mit der TypeScript-Server-Prozess und eine JSON-Nutzlast, die durch das debuggerprotokoll V8 inspiriert für Anforderungen und Antworten verwendet. Der TypeScript-Server wurde in der TypeScript-Sublime-Plug-in und Visual Studio Code zum Bearbeiten von rich TypeScript integriert.

Nach müssen integriert zwei andere Sprache-Servern, gestartet im VS Code-Team eine allgemeine sprachserverprotokoll für Editoren und IDEs zu untersuchen. Ein häufig verwendetes Protokoll ermöglicht einen Sprachanbieter für eine einzelne Sprache-Server zu erstellen, der von anderen IDEs genutzt werden können. Ein Sprache-Server-Consumer muss nur einmal der Clientseite des Protokolls zu implementieren. Dies führt in einer Win-Win-Situation für den Sprachanbieter und der Language-Consumer.

Das sprachserverprotokoll, die mit dem Protokoll verwendet wird, durch den TypeScript-Server, erweitern es mit mehr Sprachfeatures, die sich inspirieren, von der Sprache der Visual Studio Code-API-wurde gestartet. Das Protokoll wird mit JSON-RPC für Remoteaufruf aufgrund seiner Einfachheit und vorhandene Bibliotheken gesichert.

Die VS Code Team Prototyp des Protokolls durch die Implementierung von mehrere Language Linter Servern, die auf Antworten auf Lint (Überprüfung) fordert eine Datei, und geben Sie einen Satz von erkannte Warnungen und Fehler zurück. Ziel war es, Lint eine Datei als die benutzerbearbeitungen in einem Dokument, das bedeutet, dass viele Linting-Anforderungen während einer editorsitzung stehen. Vereinfacht sinnvoll, halten Sie einen Server einrichten und ausführen, damit ein neuer Linting-Prozess nicht gestartet werden, damit jeder Benutzer bearbeiten muss. Mehrere Server für linting-Funktion implementiert wurden, einschließlich Visual Studio Code Erweiterungen ESLint und TSLint. Dieser beiden Server für die linting-Funktion sind sowohl in TypeScript und JavaScript implementiert, und führen Sie auf Node.js. Sie teilen eine Bibliothek, die der Client und Server Teil des Protokolls implementiert.

## <a name="how-the-lsp-works"></a>Wie funktioniert die LSP

Ein Sprache-Server, die in einem eigenen Prozess ausgeführt wird, und Tools wie Visual Studio oder Visual Studio Code mit dem Server, die mithilfe des Language-Protokolls über JSON-RPC kommunizieren. Ein weiterer Vorteil der Sprache des Serverbetriebssystems in einem dedizierten Prozess ist, dass Leistungsprobleme im Zusammenhang mit einer einzelnen Prozessmodell vermieden werden. Der tatsächliche Transportkanal kann Stdio, Sockets, benannte Pipes oder Knoten Ipc entweder sein, wenn sowohl die Client-als auch in Node.js geschrieben werden.

Im folgenden ist ein Beispiel für die ein Tool und eine Sprache-Server bei einer Routine Kommunikation zwischen Sitzung bearbeiten:

![LSP-Flussdiagramm](media/lsp-flow-diagram.png)

* **Der Benutzer öffnet eine Datei (als Dokument bezeichnet) im Tool**: Das Tool wird der Sprache-Server benachrichtigt, dass ein Dokument geöffnet ist ("TextDocument/DidOpen"). Von nun an die Wahrheit über den Inhalt des Dokuments ist nicht mehr im Dateisystem jedoch vom Tool im Arbeitsspeicher beibehalten.

* **Der Benutzer trifft Bearbeitungen**: Das Tool benachrichtigt den Server über die Dokument-Änderung (' TextDocument/DidChange"), und die semantische Informationen des Programms durch die Language-Server aktualisiert wird. Wie in diesem Fall wird der Language-Server diese Informationen werden analysiert, und benachrichtigt das Tool mit dem erkannten Fehler und Warnungen ("TextDocument/PublishDiagnostics").

* **Der Benutzer führt die "Gehe zu Definition" auf ein Symbol im Editor**: Das Tool sendet eine Anforderung "TextDocument/Definition" mit zwei Parametern: (1) der Dokument-URI und (2) die Position im Text aus, in dem der zum Aufrufen der Anforderung der Anwendungsdefinition an den Server initiiert wurde. Der Server antwortet mit dem Dokument-URI und die Position der Definition des Symbols, innerhalb des Dokuments.

* **Der Benutzer schließt das Dokument (Datei)**: Eine "TextDocument/DidClose" Benachrichtigung wird gesendet, aus dem Tool, den Language-Server, den das Dokument ist nun nicht mehr im Arbeitsspeicher und, die den aktuellen Inhalt ist nun auf dem Dateisystem auf dem neuesten Stand zu informieren.

In diesem Beispiel wird veranschaulicht, wie das Protokoll mit dem Language-Server, auf der Ebene der Editor-Funktionen wie "Gehe zu Definition", "Alle Verweise suchen" kommuniziert. Die Datentypen, die vom Protokoll verwendete sind-Editor oder IDE "Datentypen", wie das aktuell geöffneten Textdokument und die Position des Cursors. Die Datentypen sind nicht auf der Ebene der einer Sprache Domäne Programmiermodell, das in der Regel die abstrakte Syntaxstrukturen und Compiler-Symbole (z. B. aufgelösten Typen, Namespaces,...) bieten würde. Dadurch wird das Protokoll erheblich vereinfacht.

Jetzt sehen wir uns die Anforderung "TextDocument/Definition" im Detail. Im folgenden sind die Nutzlasten, die zwischen dem Clienttool und das Language-Server für die Anforderung "Gehe zu Definition" in einem C++-Dokument zu wechseln.

Dies ist die Anforderung:

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

Dies ist die Antwort:

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

Rückblickend ist, beschreibt die Datentypen, die auf der Ebene des Editors und nicht auf der Ebene des Programmiermodells Sprache eine der Ursachen für den Erfolg der sprachserverprotokoll. Es ist viel einfacher, ein Textdokument URI zu standardisieren, oder die Cursorposition im Vergleich mit Standardisierung eine abstrakte Syntax-Struktur und Compiler-Symbole in verschiedenen Programmiersprachen.

Wenn ein Benutzer mit verschiedenen Sprachen funktioniert, startet Visual Studio Code in der Regel einen Sprache-Server für jede der Programmiersprachen. Das folgende Beispiel zeigt eine Sitzung, in denen der Benutzer Java-und SASS arbeitet.

![Java und sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funktionen

Nicht jede Sprache-Server unterstützen alle Features, die durch das Protokoll definiert. Client und Server gibt daher festgelegtem unterstütztes Feature über "Capabilities" bekannt. Als Beispiel kündigt ein Server, kann er die Anforderung "TextDocument/Definition" verarbeiten, aber er möglicherweise nicht die Anforderung "Arbeitsbereich/Symbol" behandelt. Auf ähnliche Weise können Clients ankündigen, dass sie zu "zum Speichern" können Benachrichtigungen, bevor ein Dokument gespeichert wird, damit ein Server Text Änderungen zum automatischen Formatieren von das bearbeitete Dokument berechnen,.

## <a name="integrating-a-language-server"></a>Die Integration von eine Sprache-server

Die eigentliche Integration eines Sprache-Servers zu einem bestimmten Tool wird nicht durch das sprachserverprotokoll definiert und ist das Tool Implementierer überlassen. Einige Tools integrieren Sprache Server generisch, dass eine Erweiterung, die gestartet und für jede Art von Sprache-Server kommunizieren kann. Andere erstellen wie Visual Studio Code, eine benutzerdefinierte Erweiterung pro Sprache-Server, damit eine Erweiterung noch einige Funktionen für die benutzerdefinierte Sprache ist.

Um die Implementierung von Sprache-Servern und Clients zu vereinfachen, sind es Bibliotheken oder SDKs für den Client und Server teilen. Diese Bibliotheken werden für verschiedene Sprachen bereitgestellt. Ist es z. B. eine [Npm-Clientmodul Sprache](https://www.npmjs.com/package/vscode-languageclient) zum Vereinfachen der Integration von eine Sprache-Server in einer Visual Studio Code-Erweiterung und ein anderes [Npm-Moduls für Sprache Server](https://www.npmjs.com/package/vscode-languageserver) , schreiben einen Sprache-Server mithilfe von Node.js. Dies ist die aktuelle [Liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) Support-Bibliotheken.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Verwenden in Visual Studio das Sprachserverprotokoll

* [Hinzufügen einer Erweiterung Sprachserverprotokoll](adding-an-lsp-extension.md) -erfahren Sie mehr über die Integration von einem Server für die Sprache in Visual Studio.
