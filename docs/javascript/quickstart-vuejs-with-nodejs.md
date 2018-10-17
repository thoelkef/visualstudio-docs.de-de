---
title: 'Schnellstart: Erstellen einer ersten Vue.js-App mit Visual Studio'
description: In dieser Schnellstartanleitung erstellen Sie mit den Node.js-Tools für Visual Studio eine Vue.js-App in Visual Studio
ms.date: 09/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: b4e08b0ad058566bdd74522b94e0010d5cdc2f91
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168356"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Schnellstart: Erstellen einer ersten Vue.js-App mit Visual Studio

Mithilfe dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (Integrated, Development Environment, IDE) von Visual Studio können Sie eine einfache Vue.js-Webanwendung erstellen und ausführen. Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

> [!IMPORTANT]
> Für diesen Artikel ist die Vue.js-Vorlage erforderlich, die in Visual Studio 2017 ab Version 15.8 verfügbar ist.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die Vue.js-Webanwendung erstellen.

1. Wenn die Node.js-Runtime nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website.

    Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Laufzeit nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Laufzeit auf der Eigenschaftenseite verweist (klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus).

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Wählen Sie im Dialogfeld **Neues Projekt** unter **JavaScript** > **Node.js** oder unter **TypeScript** > **Node.js** die Option **Grundlegende Vue.js-Webanwendung** aus. Geben Sie anschließend einen Projektnamen ein, und klicken Sie auf **OK**.

     ![Vue.js-Vorlage](../javascript/media/vuejs-template.png)

    Visual Studio erstellt daraufhin das neue Projekt. Das neue Projekt wird im Projektmappen-Explorer geöffnet (im rechten Bereich).

     Falls Ihnen die Projektvorlage **Grundlegende Vue.js-Webanwendung** nicht angezeigt wird, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

     ![Node.js-Workload im VS-Installer](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt.

1. Überprüfen Sie während der Installation des npm-Pakets, das für die Anwendung erforderlich ist, im Fenster „Ausgabe“ (unterer Bereich) den Fortschritt.

1. Öffnen Sie im Projektmappen-Explorer den **npm**-Knoten, und stellen Sie sicher, dass alle aufgeführten npm-Pakete installiert wurden.

    Wenn Pakete fehlen (Ausrufezeichensymbol), klicken Sie mit der rechten Maustaste auf den **NPM**-Knoten, und wählen Sie **Fehlende NPM-Pakete installieren** aus.

## <a name="explore-the-ide"></a>Durchsuchen der IDE

1. Sehen Sie sich den **Projektmappen-Explorer** im rechten Bereich an.

     ![Vue.js-Projektmappe](../javascript/media/vuejs-solution.png)

  - Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld **Neues Projekt** festgelegt haben. Auf dem Datenträger wird dieses Projekt im Projektordner durch eine *NJSPROJ-Datei* dargestellt.

  - Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

  - Der **npm**-Knoten zeigt alle installierten npm-Pakete an. Sie können mit der rechten Maustaste darauf klicken, um über ein Dialogfeld npm-Pakete zu suchen und zu installieren.

1. Wenn Sie npm-Pakete oder Node.js-Befehle über eine Eingabeaufforderung installieren möchten, klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie anschließend auf **Eingabeaufforderung hier öffnen**.

## <a name="add-a-vue-file-to-the-project"></a>Hinzufügen einer Vue-Datei zum Projekt

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf einen beliebigen Ordner, z.B. den *SRC*-Ordner, und wählen Sie anschließend **Hinzufügen** > **Neues Element** aus.

1. Wählen sie entweder **JavaScript Vue-Einzeldateikomponente** oder **TypeScript Vue-Einzeldateikomponente** aus, und klicken Sie anschließend auf **Hinzufügen**.

    Visual Studio fügt die neue Datei zum Projekt hinzu.

## <a name="build-the-project"></a>Erstellen des Projekts

1. (Gilt nur für das TypeScript-Projekt) Wählen sie in Visual Studio die Option **Erstellen** > **Projektmappe bereinigen** aus.

1. Wählen Sie als Nächstes **Erstellen** > **Projektmappe erstellen** aus, um das Projekt zu erstellen. Überprüfen Sie das Fenster **Ausgabe**, um die Buildergebnisse anzuzeigen.

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

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über die Visual Studio-IDE mit Vue.js gelernt haben. Wenn Sie mehr über deren Funktionen erfahren möchten, können Sie gerne mit einem Tutorial im Inhaltsverzeichnis mit dem Abschnitt **Tutorials** fortfahren.

## <a name="next-steps"></a>Nächste Schritte

- Sehen Sie sich das [Tutorial zu Node.js und Express](../nodejs/tutorial-nodejs.md) an.
- Sehen Sie sich das [Tutorial zu Node.js und React](../nodejs/tutorial-nodejs-with-react-and-jsx.md) an.
- [Deploy the app to Linux App Service (Bereitstellen der App für Linux App Service)](../javascript/publish-nodejs-app-azure.md)