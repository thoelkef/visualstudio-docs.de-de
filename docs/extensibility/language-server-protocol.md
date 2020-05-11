---
title: Language Server-Protokollübersicht | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703102"
---
# <a name="language-server-protocol"></a>Sprachserverprotokoll

## <a name="what-is-the-language-server-protocol"></a>Was ist das Language Server-Protokoll?

Die Unterstützung umfangreicher Bearbeitungsfunktionen wie automatischer Hauptvervollständigungen für Quellcode oder **Go to Definition** für eine Programmiersprache in einem Editor oder einer IDE ist traditionell sehr anspruchsvoll und zeitaufwändig. In der Regel ist es erforderlich, ein Domänenmodell (einen Scanner, einen Parser, einen Typprüfer, einen Builder und mehr) in der Programmiersprache des Editors oder der IDE zu schreiben. Beispielsweise wird das Eclipse CDT-Plugin, das C/C++ in der Eclipse IDE unterstützt, in Java geschrieben, da die Eclipse IDE selbst in Java geschrieben ist. Nach diesem Ansatz würde dies bedeuten, ein C/C++-Domänenmodell in TypeScript für Visual Studio-Code und ein separates Domänenmodell in C-Code für Visual Studio zu implementieren.

Das Erstellen sprachspezifischer Domänenmodelle ist ebenfalls viel einfacher, wenn ein Entwicklungstool vorhandene sprachspezifische Bibliotheken wiederverwenden kann. Diese Bibliotheken werden jedoch in der Regel in der Programmiersprache selbst implementiert (z. B. werden gute C/C++-Domänenmodelle in C/C++ implementiert). Die Integration einer C/C++-Bibliothek in einen in TypeScript geschriebenen Editor ist technisch möglich, aber schwierig.

### <a name="language-servers"></a>Sprachserver

Ein anderer Ansatz besteht darin, die Bibliothek in einem eigenen Prozess auszuführen und die prozessübergreifende Kommunikation zu verwenden, um mit ihr zu kommunizieren. Die hin- und hersenden Nachrichten bilden ein Protokoll. Das Language Server Protocol (LSP) ist das Produkt der Standardisierung der Zwischennachrichten, die zwischen einem Entwicklungstool und einem Sprachserverprozess ausgetauscht werden. Die Verwendung von Sprachservern oder Dämonen ist keine neue oder neue Idee. Redakteure wie Vim und Emacs tun dies seit einiger Zeit, um semantische Auto-Vervollständigung Unterstützung zu bieten. Das Ziel des LSP war es, diese Art von Integrationen zu vereinfachen und einen nützlichen Rahmen für die Bereitstellung von Sprachfeatures für eine Vielzahl von Tools bereitzustellen.

Ein gemeinsames Protokoll ermöglicht die Integration von Programmiersprachenfunktionen in ein Entwicklungstool mit minimalem Aufwand, indem eine vorhandene Implementierung des Domänenmodells der Sprache wiederverwendet wird. Ein Sprachserver-Back-End könnte in PHP, Python oder Java geschrieben werden und der LSP ermöglicht es, es einfach in eine Vielzahl von Tools zu integrieren. Das Protokoll arbeitet auf einer gemeinsamen Abstraktionsebene, sodass ein Tool umfangreiche Sprachdienste anbieten kann, ohne die für das zugrunde liegende Domänenmodell spezifischen Nuancen vollständig verstehen zu müssen.

## <a name="how-work-on-the-lsp-started"></a>Wie die Arbeit am LSP begann

Der LSP hat sich im Laufe der Zeit weiterentwickelt und ist heute bei Version 3.0. Es begann, als das Konzept eines Sprachservers von OmniSharp übernommen wurde, um umfangreiche Bearbeitungsfunktionen für C-Code bereitzustellen. Zunächst verwendete OmniSharp das HTTP-Protokoll mit einer JSON-Nutzlast und wurde in mehrere Editoren integriert, einschließlich [Visual Studio Code](https://code.visualstudio.com).

Etwa zur gleichen Zeit begann Microsoft mit der Arbeit an einem TypeScript-Sprachserver mit der Idee, TypeScript in Editoren wie Emacs und Sublime Text zu unterstützen. In dieser Implementierung kommuniziert ein Editor über stdin/stdout mit dem TypeScript-Serverprozess und verwendet eine JSON-Nutzlast, die vom V8-Debuggerprotokoll für Anforderungen und Antworten inspiriert ist. Der TypeScript-Server wurde in das TypeScript Sublime-Plugin und den VS-Code für die umfangreiche TypeScript-Bearbeitung integriert.

Nachdem das VS-Code-Team zwei verschiedene Sprachserver integriert hatte, begann es, ein Common Language Server-Protokoll für Editoren und IDEs zu erkunden. Ein gemeinsames Protokoll ermöglicht es einem Sprachanbieter, einen einzelnen Sprachserver zu erstellen, der von verschiedenen IDEs genutzt werden kann. Ein Sprachserver-Consumer muss die Clientseite des Protokolls nur einmal implementieren. Dies führt zu einer Win-Win-Situation sowohl für den Sprachanbieter als auch für den Sprachkonsumenten.

Das Sprachserverprotokoll begann mit dem vom TypeScript-Server verwendeten Protokoll und erweiterte es um weitere Sprachfeatures, die von der VS-Code-Sprach-API inspiriert wurden. Das Protokoll wird aufgrund seiner Einfachheit und vorhandenen Bibliotheken mit JSON-RPC für Remoteaufrufe unterstützt.

Das VS-Code-Team hat das Protokoll prototypisch erstellt, indem es mehrere Linter-Sprachserver implementiert hat, die auf Anfragen reagieren, eine Datei zu scannen und eine Reihe von erkannten Warnungen und Fehlern zurückzugeben. Das Ziel bestand darin, eine Datei zu verfeinern, während der Benutzer in einem Dokument bebaut, was bedeutet, dass es während einer Editorsitzung viele Linting-Anforderungen geben wird. Es war sinnvoll, einen Server betriebsbereit zu halten, damit nicht für jede Benutzerbearbeitung ein neuer Linting-Prozess gestartet werden musste. Mehrere Linter-Server wurden implementiert, darunter die ESLint- und TSLint-Erweiterungen von VS Code. Diese beiden linter-Server werden beide in TypeScript/JavaScript implementiert und auf Node.js ausgeführt. Sie verwenden eine Bibliothek, die den Client- und Serverteil des Protokolls implementiert.

## <a name="how-the-lsp-works"></a>Funktionsweise des LSP

Ein Sprachserver wird in einem eigenen Prozess ausgeführt, und Tools wie Visual Studio oder VS Code kommunizieren mit dem Server über das Sprachprotokoll über JSON-RPC. Ein weiterer Vorteil des Sprachservers, der in einem dedizierten Prozess arbeitet, besteht darin, dass Leistungsprobleme im Zusammenhang mit einem einzelnen Prozessmodell vermieden werden. Der eigentliche Transportkanal kann entweder stdio, Sockets, Named Pipes oder Node ipc sein, wenn sowohl der Client als auch der Server in Node.js geschrieben werden.

Im Folgenden finden Sie ein Beispiel für die Kommunikation eines Tools und eines Sprachservers während einer routinen Bearbeitungssitzung:

![lsp Strömungsdiagramm](media/lsp-flow-diagram.png)

* **Der Benutzer öffnet eine Datei (als Dokument bezeichnet) im Tool**: Das Tool benachrichtigt den Sprachserver, dass ein Dokument geöffnet ist ('textDocument/didOpen'). Von nun an ist die Wahrheit über den Inhalt des Dokuments nicht mehr auf dem Dateisystem, sondern durch das Tool im Speicher gehalten.

* **Der Benutzer nimmt Änderungen vor:** Das Tool benachrichtigt den Server über die Dokumentänderung ('textDocument/didChange') und die semantischen Informationen des Programms werden vom Sprachserver aktualisiert. In diesem Fall analysiert der Sprachserver diese Informationen und benachrichtigt das Tool mit den erkannten Fehlern und Warnungen ('textDocument/publishDiagnostics").

* **Der Benutzer führt "Zur Definition" auf einem Symbol im Editor**aus: Das Tool sendet eine 'textDocument/Definition'-Anforderung mit zwei Parametern: (1) den Dokument-URI und (2) die Textposition, von der aus die Go to Definition-Anforderung an den Server initiiert wurde. Der Server antwortet mit dem Dokument-URI und der Position der Symboldefinition im Dokument.

* **Der Benutzer schließt das Dokument (Datei):** Eine 'textDocument/didClose'-Benachrichtigung wird vom Tool gesendet, um den Sprachserver darüber zu informieren, dass sich das Dokument jetzt nicht mehr im Speicher befindet und der aktuelle Inhalt nun auf dem Dateisystem auf dem neuesten Stand ist.

Dieses Beispiel veranschaulicht, wie das Protokoll mit dem Sprachserver auf der Ebene von Editor-Features wie "Go to Definition", "Alle Referenzen suchen" kommuniziert. Die vom Protokoll verwendeten Datentypen sind Editor- oder IDE-Datentypen wie das aktuell geöffnete Textdokument und die Position des Cursors. Die Datentypen befinden sich nicht auf der Ebene eines Programmiersprachendomänenmodells, das normalerweise abstrakte Syntaxstrukturen und Compilersymbole bereitstellen würde (z. B. aufgelöste Typen, Namespaces, ...). Dies vereinfacht das Protokoll erheblich.

Sehen wir uns nun die Anfrage "textDocument/definition" genauer an. Im Folgenden finden Sie die Nutzlasten, die zwischen dem Clienttool und dem Sprachserver für die "Go to Definition"-Anforderung in einem C++-Dokument verlaufen.

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

Im Nachhinein ist die Beschreibung der Datentypen auf der Ebene des Editors und nicht auf der Ebene des Programmiersprachenmodells einer der Gründe für den Erfolg des Sprachserverprotokolls. Es ist viel einfacher, einen Textdokument-URI oder eine Cursorposition zu standardisieren, verglichen mit der Standardisierung einer abstrakten Syntaxstruktur und Compilersymbolen in verschiedenen Programmiersprachen.

Wenn ein Benutzer mit verschiedenen Sprachen arbeitet, startet VS Code in der Regel einen Sprachserver für jede Programmiersprache. Das folgende Beispiel zeigt eine Sitzung, in der der Benutzer an Java- und SASS-Dateien arbeitet.

![java und sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funktionen

Nicht jeder Sprachserver kann alle vom Protokoll definierten Funktionen unterstützen. Daher geben Client und Server ihre unterstützte Funktion über "Funktionen" bekannt. Ein Server kündigt beispielsweise an, dass er die "textDocument/definition"-Anforderung verarbeiten kann, aber möglicherweise nicht die "workspace/symbol"-Anforderung. Ebenso können Clients ankündigen, dass sie Benachrichtigungen zum Speichern bereitstellen können, bevor ein Dokument gespeichert wird, sodass ein Server Textänderungen berechnen kann, um das bearbeitete Dokument automatisch zu formatieren.

## <a name="integrating-a-language-server"></a>Integration eines Sprachservers

Die tatsächliche Integration eines Sprachservers in ein bestimmtes Tool wird nicht durch das Sprachserverprotokoll definiert und den Toolimplementierern überlassen. Einige Tools integrieren Sprachserver generisch, indem sie über eine Erweiterung verfügen, die jede Art von Sprachserver starten und mit ihnen kommunizieren kann. Andere, wie VS Code, erstellen eine benutzerdefinierte Erweiterung pro Sprachserver, sodass eine Erweiterung immer noch einige benutzerdefinierte Sprachfeatures bereitstellen kann.

Um die Implementierung von Sprachservern und Clients zu vereinfachen, gibt es Bibliotheken oder SDKs für den Client und die Serverteile. Diese Bibliotheken werden für verschiedene Sprachen bereitgestellt. Beispielsweise gibt es ein [Sprachclient-npm-Modul,](https://www.npmjs.com/package/vscode-languageclient) um die Integration eines Sprachservers in eine VS-Code-Erweiterung zu vereinfachen, und ein anderes [npm-Modul des Sprachservers,](https://www.npmjs.com/package/vscode-languageserver) um einen Sprachserver mit Node.js zu schreiben. Dies ist die aktuelle [Liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) der Supportbibliotheken.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Verwenden des Language Server-Protokolls in Visual Studio

* [Hinzufügen einer Language Server Protocol-Erweiterung](adding-an-lsp-extension.md) – Erfahren Sie mehr über die Integration eines Sprachservers in Visual Studio.
