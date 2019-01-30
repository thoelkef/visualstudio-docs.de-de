---
title: Debuggen einer JavaScript- oder TypeScript-App
description: Visual Studio unterstützt das Debuggen JavaScript- and TypeScript-Apps in Visual Studio
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f3b2e3c5179c5edb390fc494b49ba0051e04108e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995057"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Debuggen einer JavaScript- oder TypeScript-App in Visual Studio

Sie können mithilfe von Visual Studio JavaScript- und TypeScript-Code debuggen. Sie können Breakpoints festlegen und erreichen, den Debugger anfügen, Variablen untersuchen, die Aufrufliste anzeigen und andere Debugfeatures verwenden.

> [!TIP]
> Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen. Je nachdem, welche Art von App-Entwicklung Sie wählen, müssen Sie die **Workload für die Node.js-Entwicklung** zusammen mit Visual Studio installieren.

## <a name="debug-server-side-script"></a>Debuggen von serverseitigen Skripts

1. Öffnen Sie zunächst Ihr Projekt in Visual Studio und anschließend eine serverseitige JavaScript-Datei (z. B. *server.js*). Klicken Sie dann auf den Bundsteg auf der linken Seite, um einen Breakpoint festzulegen:

    ![Haltepunkt festlegen](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die App auszuführen.

    Der Debugger hält an dem von Ihnen festgelegten Haltepunkt an (die aktuelle Anweisung ist gelb gekennzeichnet). Jetzt können Sie den App-Status überprüfen, indem Sie auf die derzeitigen Variablen im Bereich zeigen. Verwenden Sie dafür Debuggerfenster wie **Lokal** und **Überwachen**.

1. Drücken Sie **F5**, um die App fortzusetzen.

1. Wenn Sie die Chrome-Entwicklertools oder die F12-Tools verwenden möchten, drücken Sie **F12**. Mit diesen Tools können Sie das DOM untersuchen und mithilfe der JavaScript-Konsole mit der App interagieren.

## <a name="debug-client-side-script"></a>Debuggen von clientseitigen Skripts

Visual Studio unterstützt das Debuggen nur für Chrome und Internet Explorer. In einigen Szenarios erreicht der Debugger automatisch Breakpoints in JavaScript- und TypeScript-Code sowie in Skripts, die in HTML-Dateien eingebettet sind.

Wenn Ihre Quelle verkleinert oder von einem Transpiler wie TypeScript oder Babel erstellt wird, sollten [Quellzuordnungen](#generate_sourcemaps) verwendet werden, um beim Debuggen die bestmöglichen Ergebnisse zu erzielen. Wenn keine Quellzuordnungen verwendet werden, können Sie allerdings immer noch den Debugger an ein clientseitiges Skript anfügen, das zu diesem Zeitpunkt ausgeführt wird. Es kann aber vorkommen, dass Sie Breakpoints nicht in der ursprünglichen Quelldatei, sondern nur in der verkleinerten oder transpilierten Datei festlegen oder erreichen können. In einer Vue.js-App werden verkleinerte Skripts beispielsweise als Zeichenfolgen an eine `eval`-Anweisung übergeben, und Sie können den Code nur erfolgreich mithilfe des Visual Studio-Debuggers durchgehen, wenn Sie Quellzuordnungen verwenden. Möglicherweise verwenden Sie in einigen komplexen Debugszenarios auch Chrome-Entwicklertools oder F12-Tools für Microsoft Edge.

Wenn der Debugger von Visual Studio angehängt und Breakpoints im clientseitigen Code erreicht werden sollen, benötigt dieser in der Regel Hilfe beim Identifizieren des richtigen Prozesses. Sie können dafür z. B. in Chrome wie im folgenden Abschnitt beschrieben vorgehen.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Anfügen des Debuggers an clientseitige Skripts mithilfe von Chrome

1. Schließen Sie alle Chrome-Fenster.

    Dies ist notwendig, damit Sie Chrome im Debugmodus ausführen können.

2. Öffnen Sie über das Windows-**Startmenü** den Befehl **Ausführen** (klicken Sie mit der rechten Maustaste auf die Schaltfläche, und wählen Sie **Ausführen** aus), und geben Sie den folgenden Befehl ein:

    `chrome.exe --remote-debugging-port=9222`

    Dadurch wird Chrome mit aktiviertem Debuggen gestartet.

3. Wechseln Sie zu Visual Studio, und legen Sie in Ihrem Quellcode einen Breakpoint fest. (Legen Sie den Breakpoint in einer Codezeile fest, in der dies zulässig ist, also z. B. in einer `return`-Anweisung oder einer `var`-Deklaration.)

    ![Haltepunkt festlegen](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Wenn Sie in einer großen, generierten Datei einen bestimmten Codeausschnitt suchen, drücken Sie **STRG**+**F** (**Bearbeiten** > **Suchen und Ersetzen** > **Schnellsuche**).

4. Wenn Chrome bereits als Debugziel in Visual Studio ausgewählt wurde, drücken Sie **STRG**+**F5** (**Debuggen** > **Starten ohne Debuggen**), um die App im Browser auszuführen.

    Die App wird daraufhin in einer neuen Registerkarte im Browser geöffnet.

    Wenn Chrome auf Ihrem Computer verfügbar ist, jedoch nicht als Option angezeigt wird, wählen Sie aus der Dropdownliste für das Debugziel **Browserauswahl** aus, und klicken Sie dann auf Chrome, um diesen Browser als Standardbrowser festzulegen (wählen Sie dazu **Als Standard festlegen** aus).

5. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

6. Wählen Sie im Dialogfeld **An den Prozess anhängen** im Feld **Anfügen an** den Eintrag **WebKit code** (WebKit-Code) aus. Geben Sie in das Filterfeld **Chrome** ein, um die Suchergebnisse zu filtern.

    WebKitDer Wert **WebKit code** (WebKit-Code) ist für Chrome erforderlich, dabei es sich dabei um einen auf WebKit basierenden Browser handelt.

7. Wählen Sie den Chrome-Prozess mit dem richtigen Hostport aus (1337 auf der folgenden Abbildung), und klicken Sie auf **Anfügen**.

    ![Anhängen an den Prozess](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Der Debugger wurde ordnungsgemäß angehängt, wenn DOM Explorer und die JavaScript-Konsole in Visual Studio geöffnet werden. Diese Debugtools ähneln den Chrome-Entwicklertools und den F12-Tools für Microsoft Edge.

    > [!NOTE]
    > Wenn der Debugger nicht angefügt wird, und die Meldung „Das Anfügen an den Prozess ist nicht möglich. Ein Vorgang ist für den derzeitigen Zustand unzulässig.“ angezeigt wird, verwenden Sie den Task-Manager, um alle Instanzen von Chrome zu schließen, bevor Sie den Browser im Debugmodus starten. Möglicherweise werden Chrome-Erweiterungen ausgeführt, die den vollständigen Debugmodus verhindern.

8. Da der Code mit dem Breakpoint bereits ausgeführt wurde, aktualisieren Sie die Browserseite, um diesen zu erreichen.

    Während der Unterbrechung im Debugger können Sie den App-Status überprüfen, indem Sie mit dem Mauszeiger auf Variablen zeigen und Debuggerfenster verwenden. Sie können den Debugger durch Navigieren im Code nach vorne verschieben (**F5**, **F10** und **F11**).

    Bei verkleinertem oder transpiliertem JavaScript-Code erreichen Sie den Breakpoint entweder in der transpilierten JavaScript-Datei oder (unter Verwendung von Quellzuordnungen) an deren zugeordnetem Speicherort in der TypeScript-Datei. Dies ist von Ihrer Umgebung und dem Browserstatus abhängig. In beiden Fällen können Sie durch den Code navigieren und Variablen überprüfen.

    * Wenn Sie in einer TypeScript-Datei Code unterbrechen müssen, dies aber nicht möglich ist, verwenden Sie wie in den vorherigen Schritten beschrieben die Option **An den Prozess anhängen**, um den Debugger anzufügen. Öffnen Sie dann im Projektmappen-Explorer die dynamisch generierte TypeScript-Datei, indem Sie **Skriptdokumente** > **Dateiname.tsx** öffnen, einen Breakpoint festlegen und die Seite in Ihrem Browser aktualisieren. (Legen Sie den Breakpoint in einer Codezeile fest, in der dies erlaubt ist, also z. B. in einer `return`-Anweisung oder einer `var`-Deklaration.)

        Stattdessen können Sie auch die `debugger;`-Anweisung in der TypeScript-Datei verwenden oder Breakpoints in den Chrome-Entwicklertools festlegen, wenn Sie Code in einer TypeScript-Datei unterbrechen müssen, dies jedoch nicht möglich ist.

    * Wenn Sie Code in einer transpilierten JavaScript-Datei (z. B. *app-bundle.js*) unterbrechen müssen, dies jedoch nicht möglich ist, entfernen Sie die Quellzuordnungsdatei *Dateiname.js.map*.

     > [!TIP]
     > Sobald Sie mit diesen Schritten erstmalig an den Prozess angehängt haben, können Sie in Visual Studio 2017 schnell erneut an diesen Prozess anhängen, indem Sie **Debuggen** > **Erneut an Prozess anhängen** auswählen.

## <a name="generate_sourcemaps"></a> Generieren von Quellzuordnungen zum Debuggen

In Visual Studio sind Funktionen zum Verwenden und Generieren von Quellzuordnungen für JavaScript-Quelldateien verfügbar. Diese werden häufig benötigt, wenn eine Quelle verkleinert oder von einem Transpiler wie TypeScript oder Babel erstellt wird. Die verfügbaren Optionen sind vom Projekttyp abhängig.

* Ein TypeScript-Projekt in Visual Studio generiert die Quellzuordnungen standardmäßig.

* In einem JavaScript-Projekt müssen Sie Quellzuordnungen mithilfe eines Bundlers wie Webpack und einem Compiler wie TypeScript (oder Babel) erstellen und anschließend zu Ihrem Projekt hinzufügen. Für den TypeScript-Compiler müssen Sie außerdem eine *tsconfig.json*-Datei hinzufügen. Unter [Create a Node.js app with React (Erstellen einer Node.js-App mit React)](../javascript/tutorial-nodejs-with-react-and-jsx.md) wird dieser Vorgang in einem Beispiel mit einer einfachen Webpack-Konfiguration erläutert.

> [!NOTE]
> Wenn Sie sich noch nicht mit Quellzuordnungen auskennen, lesen Sie zunächst den Artikel [Introduction to JavaScript Source Maps (Einführung in JavaScript-Quellzuordnungen)](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/), bevor Sie fortfahren.

Verwenden Sie zum Konfigurieren von erweiterten Einstellungen für Quellzuordnungen entweder die *tsconfig.json*-Datei oder die Projekteinstellungen in einem TypeScript-Projekt, aber nicht beides zusammen.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Konfigurieren von Quellzuordnungen mithilfe einer „tsconfig.json“-Datei

Wenn Sie eine *tsconfig.json*-Datei zu Ihrem Projekt hinzufügen, behandelt Visual Studio den Verzeichnisstamm wie ein TypeScript-Projekt. Klicken Sie erst mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer und anschließend mit der linken auf **Hinzufügen > Neues Element > Web > Skripts > TypeScript-JSON-Konfigurationsdatei**, um die Datei hinzuzufügen. Dann wird eine der folgenden Datei ähnlichen *tsconfig.json*-Datei zu Ihrem Projekt hinzugefügt.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Compileroptionen für „tsconfig.json“-Dateien

* **inlineSourceMap**: Gibt eine einzelne Datei mit Quellzuordnungen aus, anstatt separate Quellzuordnungen für jede Quelldatei zu erstellen.
* **inlineSources**: Gibt die Quelle neben den Quellzuordnungen innerhalb einer einzelnen Datei aus. Dafür müssen die Optionen *inlineSourceMap* oder *sourceMap* festgelegt sein.
* **mapRoot**: Gibt anstelle des Standardspeicherorts den Speicherort an, an dem der Debugger die Quellzuordnungsdateien (*.map*) finden sollte. Verwenden Sie dieses Flag, wenn die *MAP*-Laufzeitdateien an einem anderen Ort als die *JS*-Dateien gespeichert werden müssen. Der angegebene Speicherort ist in die Quellzuordnung eingebettet, damit der Debugger zum Speicherort der *MAP*-Dateien weitergeleitet wird.
* **sourceMap**: Generiert eine entsprechende *MAP*-Datei.
* **sourceRoot**: Gibt anstelle der Quellspeicherorte den Speicherort an, an dem der Debugger die TypeScript-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die Laufzeitquellen an einem anderen Ort als an dem Speicherort zur Entwurfszeit gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die Quelldateien befinden.

Weitere Informationen zu Compileroptionen finden Sie auf der Seite [Compiler Options (Compileroptionen)](https://www.typescriptlang.org/docs/handbook/compiler-options.html) im TypeScript-Handbuch.

### <a name="configure-source-maps-using-project-settings"></a>Konfigurieren von Quellzuordnungen mithilfe von Projekteinstellungen

Sie können die Einstellungen für die Quellzuordnungen auch mithilfe von Projekteigenschaften konfigurieren, indem Sie erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Projekt > Eigenschaften > TypeScript-Build > Debuggen** klicken.

Es sind die folgenden Projekteinstellungen verfügbar:

* **Quellzuordnungen generieren** (entspricht der Option **sourceMap** in *tsconfig.json*-Dateien): Generiert die entsprechende *MAP*-Datei.
* **Stammverzeichnis von Quellzuordnungen angeben** (entspricht der Option **mapRoot** in *tsconfig.json*-Dateien): Gibt anstelle der generierten Speicherorte den Speicherort an, an dem der Debugger die MAP-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die *MAP*-Laufzeitdateien an einem anderen Ort als die JS-Dateien gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die MAP-Dateien befinden.
* **Stammverzeichnis von TypeScript-Dateien angeben** (entspricht der Option **sourceRoot** in *tsconfig.json*-Dateien): Gibt anstelle von Quellspeicherorten den Speicherort an, an dem der Debugger die TypeScript-Dateien finden sollte. Verwenden Sie dieses Flag, wenn die Quelldateien zur Laufzeit an einem anderen Ort als zur Entwurfszeit gespeichert werden müssen. Der angegebene Speicherort wird in die Quellzuordnung eingebettet, um den Debugger an den Ort weiterzuleiten, an dem sich die Quelldateien befinden.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debuggen von JavaScript in dynamischen Dateien mithilfe von Razor (ASP.NET)

Visual Studio unterstützt das Debuggen nur für Chrome und Internet Explorer. Breakpoints werden automatisch JavaScript- bzw. TypeScript-Code und in HTML-Dateien eingebetteten Skripts angefügt.

Dynamisch generierte Dateien werden nicht automatisch gedebuggt. Außerdem können Breakpoints in Dateien, die mit einer Razor-Syntax erstellt wurden (CSHTML, VBHTML), nicht automatisch erreicht werden. Sie haben zwei Möglichkeiten, diese Art von Datei zu debuggen:

* **Platzieren Sie die `debugger;`-Anweisung an der Stelle, an der Sie den Code unterbrechen möchten:** Dadurch wird die Ausführung des dynamischen Skripts angehalten und der Debugvorgang sofort während der Erstellung gestartet.
* **Laden Sie die Seite, und öffnen Sie das dynamische Dokument in Visual Studio:** Sie müssen die dynamische Datei während des Debuggens öffnen, einen Breakpoint festlegen und anschließend die Seite aktualisieren, damit diese Methode funktioniert. Je nachdem, ob Sie Chrome oder Internet Explorer verwenden, finden Sie die Datei wie folgt:

   Bei Chrome: Navigieren Sie zu **Projektmappen-Explorer > Skriptdokumente > IhrSeitenname**.

    > [!NOTE]
    > Bei der Verwendung von Chrome wird möglicherweise die Meldung `no source is available between ` angezeigt.<script>` tags.` This is OK, just continue debugging.

   Bei Internet Explorer: Navigieren Sie zu **Projektmappen-Explorer > Skriptdokumente > Windows Internet Explorer > IhrSeitenname**.

Weitere Informationen finden Sie unter [Client-side debugging of ASP.NET projects in Google Chrome (Clientseitiges Debuggen von ASP.NET-Projekten in Google Chrome)](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/).
