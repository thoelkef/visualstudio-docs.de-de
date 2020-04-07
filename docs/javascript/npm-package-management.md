---
title: Verwalten von npm-Paketen
description: Dank Visual Studio können Sie Pakete mit dem Node.js-Paket-Manager (NPM) verwalten.
ms.custom: seodec18
ms.date: 03/12/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dba657d30eedef26337c708e7ede6c5ab85ed4cc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549959"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Verwalten von NPM-Paketen in Visual Studio

Mit NPM können Sie Pakete zur Verwendung in Ihren Node.js-Anwendungen installieren und verwalten. Visual Studio erleichtert die Interaktion mit NPM sowie die Ausführung von NPM-Befehlen über die Benutzeroberfläche oder direkt. Wenn Sie mit NPM nicht vertraut sind und weitere Informationen benötigen, wechseln Sie zur [NPM-Dokumentation](https://docs.npmjs.com/).

Die Visual Studio-Integration mit npm variiert je nach Projekttyp.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Öffnen von Ordnern (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> Von npm wird erwartet, dass der Ordner *node_modules* und *package.json* im Projektstamm vorhanden sind. Wenn sich die Ordnerstruktur Ihrer App unterscheidet, sollten Sie Ihre Ordnerstruktur anpassen, wenn Sie npm-Pakete mit Visual Studio verwalten.

> [!NOTE]
> Verwenden Sie für vorhandene Node.js-Projekte die Projektmappenvorlage **Aus vorhandenem Node.js-Code**, um npm in Ihrem Projekt zu aktivieren.

## <a name="nodejs-projects"></a>Node.js-Projekte

Verwenden Sie bei Node.js-Projekten eine der folgenden Methoden:
* [Installieren von Paketen über den Projektmappen-Explorer](#npmInstallWindow)
* [Verwalten von installierten Paketen über den Projektmappen-Explorer](#solutionExplorer)
* [Verwenden des Befehls `.npm` im interaktiven Node.js-Fenster](#interactive)

Diese Features arbeiten zusammen und werden mit dem Projektsystem und der Datei *package.json* im Projekt synchronisiert.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Installieren von Paketen über den Projektmappen-Explorer (Node.js)

Die npm-Pakete lassen sich bei Node.js-Projekten am einfachsten über das npm-Paketinstallationsfenster installieren. Um dieses Fenster aufzurufen, klicken Sie im Projekt mit der rechten Maustaste auf den Knoten **NPM**. Wählen Sie anschließend die Option **Neue NPM-Pakete installieren** aus.

![Installieren eines neuen NPM-Pakets über den Projektmappen-Explorer](../javascript/media/solution-explorer-install-package.png)

In diesem Fenster können Sie nach einem Paket suchen sowie Optionen angeben und installieren.

![Suchen nach einem NPM-Paket](../javascript/media/search-package.png)

* **Abhängigkeitstyp**: Wählen Sie zwischen den Paketen **Standard**, **Entwicklung** und **Optional**. „Standard“ gibt an, dass es sich bei dem Pakte um eine Laufzeitabhängigkeit handelt, während „Entwicklung“ angibt, dass das Paket nur während der Entwicklung benötigt wird.
* **Zu „package.json“ hinzufügen**: Diese Option ist veraltet.
* **Ausgewählte Version**: Wählen Sie die Version des Pakets aus, die Sie installieren möchten.
* **Weitere NPM-Argumente**: Geben Sie weitere NPM-Standardargumente an. Sie können beispielsweise einen Versionswert wie `@~0.8` eingeben, um eine bestimmte Version zu installieren, die in der Versionsliste nicht verfügbar ist.

Der Fortschritt der Installation wird in der **npm**-Ausgabe im Fenster **Ausgabe** angezeigt. Dieser Vorgang kann einige Zeit dauern.

![npm-Ausgabe](../javascript/media/npm-output.png)

> [!TIP]
> Sie können nach bereichsbezogenen Paketen suchen, indem Sie die Suchabfrage mit dem für Sie interessanten Bereich voranstellen. Geben Sie beispielsweise `@types/mocha` ein, um nach TypeScript-Definitionsdateien für Mocha zu suchen. Wenn Sie Typdefinitionen für TypeScript installieren, können Sie die TypeScript-Version angeben, die Sie als Ziel verwenden. Fügen Sie hierzu `@ts2.6` im npm-Argumentfeld hinzu.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Verwalten von installierten Paketen über den Projektmappen-Explorer (Node.js)

NPM-Pakete werden im Projektmappen-Explorer angezeigt. Die Einträge unter dem Knoten **NPM** stellt die Abhängigkeiten in der Datei *package.json* dar.

![Suchen nach einem NPM-Paket](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paketstatus

* ![Installiertes Paket](../javascript/media/installed-npm.png) - In „package.json“ installiert und aufgeführt
* ![Nicht relevantes Paket](../javascript/media/extraneous-npm.png): Installiert, aber in „package.json“ nicht explizit aufgeführt
* ![Fehlendes Paket](../javascript/media/missing-npm.png) - Nicht installiert, aber in „package.json“ aufgeführt

Klicken Sie mit der rechten Maustaste auf einen Paketknoten oder auf den Konten **NPM**, um eine der folgenden Aktionen durchzuführen:
* **Fehlende Pakete installieren**, die in *package.json* aufgeführt sind
* **Pakete aktualisieren** auf die neueste Version
* **Paket deinstallieren** und in *package.json* entfernen

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Verwenden des Befehls „.npm“ im interaktiven Node.js-Fenster (Node.js)

Zum Ausführen von NPM-Befehlen können Sie auch den Befehl `.npm` im interaktiven Node.js-Fenster verwenden. Klicken Sie zum Öffnen des Fensters mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie **Interaktives Node.js-Fenster** aus.

In diesem Fenster können Sie Befehle wie die folgenden zum Installieren eines Pakets verwenden:

`.npm install azure@4.2.3`

 > [!Tip]
 > NPM wird standardmäßig im Basisverzeichnis Ihres Projekts ausgeführt. Wenn sich in Ihrer Projektmappe mehrere Projekte befinden, geben Sie den Namen oder den Pfad des Projekts in Klammern an.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Wenn in Ihrem Projekt die Datei „package.json“ nicht enthalten ist, verwenden Sie `.npm init -y`, um eine neue „package.json“-Datei mit Standardeinträgen zu erstellen.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core-Projekte

Für Projekte wie ASP.NET Core-Projekte können Sie npm-Unterstützung in Ihr Projekt integrieren und npm zum Installieren von Paketen verwenden.
* [Hinzufügen der npm-Unterstützung zu einem Projekt](#npmAdd)
* [Installieren von Paketen mit „package.json“](#npmInstallPackage)

>[!NOTE]
> Für ASP.NET Core-Projekte können Sie auf den [Bibliotheks-Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) oder YARN anstelle von npm verwenden, um clientseitige JavaScript- und CSS-Dateien zu installieren.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Hinzufügen der npm-Unterstützung zu einem Projekt (ASP.NET Core)

Wenn Ihr Projekt noch keine *package.json*-Datei enthält, können Sie diese zu Ihrem Projekt hinzufügen, um die npm-Unterstützung zu aktivieren.

1. Klicken Sie zum Hinzufügen der Datei mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt, und wählen Sie dann **Hinzufügen** > **Neues Element** aus. Wählen Sie dann die **npm-Konfigurationsdatei** aus, bestätigen Sie den Standardnamen, und klicken Sie dann auf **Hinzufügen**.

   ![Hinzufügen der Datei „package.json“ zu Ihrem Projekt](../javascript/media/npm-add-package-json.png)

1. Fügen Sie mindestens ein npm-Paket in den `dependencies`- oder `devDependencies`-Abschnitt von *package.json* ein. Beispielsweise können Sie Folgendes zur Datei hinzufügen:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Wenn Sie die Datei speichern, fügt Visual Studio das Paket unter dem Knoten **Dependencies/npm** (Abhängigkeiten/npm) im Projektmappen-Explorer hinzu. Wenn der Knoten nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf die Datei **package.json**, und wählen Sie dann **Pakete wiederherstellen** aus.

>[!NOTE]
> In einigen Szenarios gibt der Projektmappen-Explorer möglicherweise an, dass ein npm-Paket nicht mit der Datei *package.json* synchron ist. Dies liegt an einem bekannten Fehler, der [hier](https://github.com/aspnet/Tooling/issues/479) beschrieben wird. Beispielsweise wird das Paket möglicherweise als nicht installiert angezeigt, obwohl es installiert ist. In den meisten Fällen können Sie den Projektmappen-Explorer aktualisieren, indem Sie die Datei *package.json* löschen, Visual Studio neu starten und die Datei *package.json* wie zuvor im Artikel beschrieben wieder hinzufügen.

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installieren von Paketen mit „package.json“ (ASP.NET Core)

Bei Projekten, in die npm integriert ist, können Sie npm-Pakete mit `package.json` konfigurieren. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den npm-Knoten, und wählen Sie dann **package.json öffnen** aus.

![Suchen nach einem NPM-Paket](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* unterstützt Sie bei der Auswahl einer spezifischen Version eines npm-Pakets.

![Suchen nach einem NPM-Paket](../javascript/media/npm-add-package-intellisense.png)

Wenn Sie die Datei speichern, fügt Visual Studio das Paket unter dem Knoten **Dependencies/npm** (Abhängigkeiten/npm) im Projektmappen-Explorer hinzu. Wenn der Knoten nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf die Datei **package.json**, und wählen Sie dann **Pakete wiederherstellen** aus.

Die Installation eines Pakets kann mehrere Minuten dauern. Sie können den Fortschritt der Paketinstallation überprüfen, indem Sie zur **npm-Ausgabe** im Fenster **Ausgabe** wechseln.

![npm-Ausgabe](../javascript/media/npm-output.png)

