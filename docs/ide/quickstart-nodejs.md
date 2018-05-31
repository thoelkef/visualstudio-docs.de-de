---
title: 'Schnellstart: Erstellen einer ersten Node.js-App mit Visual Studio'
description: In diesem Schnellstart erstellen Sie eine Node.js-App in Visual Studio
ms.date: 11/15/2017
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
ms.openlocfilehash: 0a78f9fdfd1ea3612d86432619c463d526eed5c2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454039"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Schnellstart: Erstellen einer ersten Node.js-App mit Visual Studio

Mithilfe dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio können Sie eine einfache Node.js-Webanwendung erstellen. Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts
Zunächst müssen Sie ein Projekt für die Node.js-Webanwendung erstellen.

1. Wenn die Node.js-Runtime nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website.

    Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Laufzeit nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Laufzeit auf der Eigenschaftenseite verweist (klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus).

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **JavaScript**, und klicken Sie auf **Node.js**. Klicken Sie im mittleren Bereich auf **Leere Node.js-Webanwendung** und anschließend auf **OK**.

     Falls Sie die Projektvorlage **Leere Node.js-Webanwendung** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

     ![Node.js-Workload im VS-Installer](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt. *Server.js* wird im Editor im linken Bereich geöffnet.

## <a name="explore-the-ide"></a>Durchsuchen der IDE

1. Sehen Sie sich den **Projektmappen-Explorer** im rechten Bereich an.

   ![Projektmappen-Explorer](../ide/media/quickstart-nodejs-solution-explorer.png)

  - Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld **Neues Projekt** festgelegt haben. Auf dem Datenträger wird dieses Projekt von einer *NJSPROJ-Datei* im Projektordner dargestellt.

  - Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

  - Der npm-Knoten zeigt alle installierten npm-Pakete. Sie können mit der rechten Maustaste darauf klicken, um über ein Dialogfeld npm-Pakete zu suchen und zu installieren.

1. Wenn Sie npm-Pakete oder node.js-Befehle über eine Eingabeaufforderung installieren möchten, klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Eingabeaufforderung hier öffnen…**.

   ![Node.js-Eingabeaufforderung](../ide/media/quickstart-nodejs-command-prompt.png)

1. Klicken Sie in der Datei *server.js* im Editor (linker Bereich) auf `http.createServer`, und drücken Sie dann **F12**, oder klicken Sie im Kontextmenü (Rechtsklick) auf **Gehe zu Definition**. Über diesen Befehl gelangen Sie zur Definition der `createServer`-Funktion in *index.d.ts*.

   ![Kontextmenü „Gehe zu Definition“](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Navigieren Sie zurück zu *server.js*, positionieren Sie den Cursor am Ende der Zeichenfolge in der Codezeile `res.end('Hello World\n');`, und ändern Sie sie folgendermaßen:

    `res.end('Hello World\n' + res.connection.`

    Wenn Sie `connection.` eingeben, stellt IntelliSense Optionen für die automatische Vervollständigung des Codes bereit.

   ![IntelliSense, automatische Vervollständigung](../ide/media/quickstart-nodejs-intellisense.png)

1. Klicken Sie auf **localPort**, und geben Sie dann `);` zur Vervollständigung ein. Die Anweisung liest sich dann folgendermaßen:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Drücken Sie **STRG**+**F5**, oder klicken Sie auf **Debuggen > Starten ohne Debugging**, um die Anwendung auszuführen. Die App wird daraufhin in einem Browser geöffnet.

1. Im Browserfenster wird „Hello World“ sowie die lokale Portnummer angezeigt.

1. Schließen Sie den Webbrowser.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über die Visual Studio-IDE gelernt haben. Wenn Sie mehr über deren Funktionen erfahren möchten, können Sie gerne mit einem Tutorial im Inhaltsverzeichnis mit dem Abschnitt **Tutorials** fortfahren.

## <a name="next-steps"></a>Nächste Schritte

- Sehen Sie sich das [Tutorial zu Node.js und Express](../nodejs/tutorial-nodejs.md) an.
- Sehen Sie sich das [Tutorial zu Node.js und React](../nodejs/tutorial-nodejs-with-react-and-jsx.md) an.