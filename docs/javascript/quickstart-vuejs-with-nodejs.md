---
title: 'Schnellstart: Erstellen Ihrer ersten Vue.js-App'
description: In dieser Schnellstartanleitung erstellen Sie mit den Node.js-Tools für Visual Studio eine Vue.js-App in Visual Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: cbf0c97371270ef6c9443c7abd755bf956a465f0
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355259"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Schnellstart: Erstellen Ihrer ersten Vue.js-App mit Visual Studio

Mithilfe dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (Integrated, Development Environment, IDE) von Visual Studio können Sie eine einfache Vue.js-Webanwendung erstellen und ausführen.

> [!IMPORTANT]
> Für diesen Artikel ist die Vue.js-Vorlage erforderlich, die in Visual Studio 2017 ab Version 15.8 verfügbar ist.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio und die Workload für die Node.js-Entwicklung installiert haben.

    ::: moniker range=">=vs-2019"
    Wenn Sie Visual Studio 2019 noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
    ::: moniker-end

    Wenn Sie die Workload installieren müssen, Visual Studio aber bereits besitzen, navigieren Sie zu **Tools** > **Tools und Features abrufen…**. Dadurch wird der Visual Studio-Installer geöffnet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

    ![Node.js-Workload im VS-Installer](../ide/media/quickstart-nodejs-workload.png)

* Die Node.js-Laufzeit muss installiert sein.

    Wenn sie nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website. Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Laufzeit nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Laufzeit auf der Eigenschaftenseite verweist (klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus).

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die Vue.js-Webanwendung erstellen.

1. Wenn die Node.js-Runtime nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website.

    Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Runtime nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Runtime auf der Eigenschaftenseite verweist. Klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.

1. Öffnen Sie Visual Studio.

1. Erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **Vue.js** ein, und wählen Sie dann **Einfache Vue.js-Webanwendung** (entweder JavaScript oder TypeScript) aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **JavaScript** oder **TypeScript**, und wählen Sie dann **Node.js** aus. Wählen Sie im mittleren Bereich **Grundlegende Vue.js-Webanwendung** und anschließend **OK**.
    ::: moniker-end
    Wenn die Projektvorlage **Grundlegende Vue.js-Webanwendung** nicht angezeigt wird, müssen Sie die Workload für die **Node.js-Entwicklung** hinzufügen. Ausführliche Anweisungen dazu finden Sie in den [Voraussetzungen](#prerequisites).

    ![Vue.js-Vorlage](../javascript/media/vuejs-template.png)

    Visual Studio erstellt daraufhin das neue Projekt. Das neue Projekt wird im Projektmappen-Explorer geöffnet (im rechten Bereich).

1. Überprüfen Sie während der Installation des npm-Pakets, das für die Anwendung erforderlich ist, im Fenster „Ausgabe“ (unterer Bereich) den Fortschritt.

1. Öffnen Sie im Projektmappen-Explorer den **npm**-Knoten, und stellen Sie sicher, dass alle aufgeführten npm-Pakete installiert wurden.

    Wenn Pakete fehlen (Ausrufezeichensymbol), klicken Sie mit der rechten Maustaste auf den **NPM**-Knoten, und wählen Sie **Fehlende NPM-Pakete installieren** aus.

## <a name="explore-the-ide"></a>Durchsuchen der IDE

1. Sehen Sie sich den **Projektmappen-Explorer** im rechten Bereich an.

     ![Vue.js-Projektmappe](../javascript/media/vuejs-solution.png)

   - Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld **Neues Projekt** festgelegt haben. Auf dem Datenträger wird dieses Projekt im Projektordner durch eine *NJSPROJ-Datei* dargestellt.

   - Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

   - Der **npm**-Knoten zeigt alle installierten npm-Pakete an. Sie können mit der rechten Maustaste darauf klicken, um über ein Dialogfeld npm-Pakete zu suchen und zu installieren.

2. Wenn Sie npm-Pakete oder Node.js-Befehle über eine Eingabeaufforderung installieren möchten, klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie anschließend auf **Eingabeaufforderung hier öffnen**.

## <a name="add-a-vue-file-to-the-project"></a>Hinzufügen einer Vue-Datei zum Projekt

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf einen beliebigen Ordner, z. B. den Ordner *src/components*, und wählen Sie anschließend **Hinzufügen** > **Neues Element** aus.

1. Wählen sie entweder **JavaScript Vue-Einzeldateikomponente** oder **TypeScript Vue-Einzeldateikomponente** aus, und klicken Sie anschließend auf **Hinzufügen**.

    Visual Studio fügt die neue Datei zum Projekt hinzu.

## <a name="build-the-project"></a>Erstellen des Projekts

1. (Gilt nur für das TypeScript-Projekt) Wählen sie in Visual Studio die Option **Erstellen** > **Projektmappe bereinigen** aus.

1. Wählen Sie als Nächstes **Erstellen** > **Projektmappe erstellen** aus, um das Projekt zu erstellen. Überprüfen Sie die Buildergebnisse im **Ausgabenfenster**, und wählen Sie **Build** in der Liste **Ausgabe anzeigen von** aus.

    Die Vue.js-Projektvorlage verwendet das npm-Skript `build`, indem sie ein Postbuildereignis konfiguriert. Wenn Sie diese Einstellung ändern möchten, öffnen Sie die Projektdatei (*\<Projektname\>.njsproj*) über den Windows-Explorer, und suchen Sie nach der folgenden Codezeile:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Drücken Sie **STRG**+**F5**, oder klicken Sie auf **Debuggen > Starten ohne Debugging**, um die Anwendung auszuführen.

   In der Konsole wird Ihnen die Meldung *Development Server wird gestartet* angezeigt.

   Anschließend wird die App in einem Browser geöffnet.

   ![Im Browser ausgeführte Vue.js-App](../javascript/media/vuejs-running-app.png)

1. Schließen Sie den Webbrowser.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über die Visual Studio-IDE mit Vue.js gelernt haben. Wenn Sie mehr über deren Funktionen erfahren möchten, können Sie mit einem Tutorial im Inhaltsverzeichnis mit dem Abschnitt **Tutorials** fortfahren.

## <a name="next-steps"></a>Nächste Schritte

- Sehen Sie sich das [Tutorial zu Node.js und Express](../nodejs/tutorial-nodejs.md) an.
- Sehen Sie sich das [Tutorial zu Node.js und React](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx) an.
- [Deploy the app to Linux App Service (Bereitstellen der App für Linux App Service)](../javascript/publish-nodejs-app-azure.md)