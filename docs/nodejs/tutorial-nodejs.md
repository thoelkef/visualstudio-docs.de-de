---
title: Erstellen einer Node.js- und Express-App
description: In diesem Tutorial erfahren Sie, wie Sie mithilfe von Node.js-Tools für Visual Studio eine App erstellen.
ms.custom: ''
ms.date: 03/13/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 259524aa8f4bb20097f5f5504c890ee7f4cc3b78
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Tutorial: Erstellen einer Node.js- und Express-App in Visual Studio
In diesem Tutorial für die Visual Studio-Entwicklung erfahren Sie, wie Sie mithilfe von Node.js und Express eine einfache Node.js-Webanwendung erstellen, Code hinzufügen, einige Features der IDE kennenlernen und die App ausführen. Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Erstellen eines Node.js-Projekts
> * Hinzufügen von Code
> * Verwendung von IntelliSense
> * Ausführen der App
> * Treffen eines Haltepunkts

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio und die Workload für die Node.js-Entwicklung installiert haben.

    Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

    Falls Sie über Visual Studio bereits verfügen, aber die Workload noch installieren müssen, klicken Sie auf den Link **Visual Studio-Installer öffnen** im linken Bereich des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

* Die Node.js-Laufzeit muss installiert sein.

    Wenn sie nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website. Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wird die installierte Laufzeit nicht erkannt, können Sie das Projekt so konfigurieren, dass es auf die installierte Laufzeit auf der Eigenschaftenseite verweist (klicken Sie hierfür nach dem Erstellen des Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus).

    Dieses Tutorial wurde mit Node.js 8.10.0 getestet.

## <a name="create-a-project"></a>Erstellen eines Projekts
Zunächst müssen Sie ein Projekt für die Node.js-Webanwendung erstellen.

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt...**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich den Eintrag **JavaScript**, und klicken Sie auf **Node.js**. Klicken Sie im mittleren Bereich auf **Azure Node.js Express 4-Basisanwendung** und anschließend auf **OK**.

     Wenn die Projektvorlage **Azure Node.js Express 4-Basisanwendung** nicht angezeigt wird, müssen Sie zunächst die Workload **Node.js-Entwicklung** installieren.

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt. Die Projektdatei *app.js* wird im Editor (linker Bereich) geöffnet.

    - Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld **Neues Projekt** festgelegt haben. Im Dateisystem wird dieses Projekt durch eine *NJSPROJ*-Datei im Projektordner dargestellt. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus, um Eigenschaften und Umgebungsvariablen festzulegen, die dem Projekt zugeordnet sind. Roundtrips mit anderen Entwicklungstools sind möglich, da die Projektdatei keine benutzerdefinierte Änderungen an der Node.js-Projektquelle vornimmt.

    - Auf der oberen Ebene finden Sie eine Projektmappe, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt.

    - Der npm-Knoten zeigt alle installierten npm-Pakete. Sie können mit der rechten Maustaste darauf klicken, um über ein Dialogfeld npm-Pakete zu suchen und zu installieren.

    - Projektdateien wie z.B. *app.js* werden unter dem Projektknoten angezeigt. Die Startdatei des Projekts lautet *app.js*.

1. Öffnen Sie den **NPM**-Knoten, und stellen Sie sicher, dass alle erforderlichen NPM-Pakete vorhanden sind.

    Wenn Pakete fehlen (Ausrufezeichensymbol), klicken Sie mit der rechten Maustaste auf den **NPM**-Knoten, und wählen Sie **Fehlende NPM-Pakete installieren** aus.

## <a name="add-some-code"></a>Hinzufügen von Code

1. Öffnen Sie im Projektmappen-Explorer (rechter Bereich) den Ordner „Views“ (Ansichten) und anschließend *index.pug*.

1. Ersetzen Sie den Inhalt durch folgenden Code.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Öffnen Sie im Ordner „routes“ die Datei *index.js*.

1. Fügen Sie direkt vor dem Aufruf von `router.get` den folgenden Code hinzu:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Ersetzen Sie den Funktionsaufruf `router.get` durch den folgenden Code:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    In der Codezeile mit `res.render` befindet sich ein Fehler. Dieser muss behoben werden, bevor die App ausgeführt werden kann. Wir beheben den Fehler im nächsten Abschnitt.

## <a name="use-intellisense"></a>Verwendung von IntelliSense

1. Gehen Sie in der Datei *index.js* zur Codezeile mit `res.render`.

1. Geben Sie nach der `data`-Zeichenfolge `: get` ein. IntelliSense zeigt Ihnen daraufhin die `getData`-Funktion an. Klicken Sie auf `getData`.

    ![Verwendung von IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png)

1. Wenn Sie das Komma (`,`) vor `"data"` entfernen, wird die Syntax im Ausdruck grün unterkringelt. Zeigen Sie auf die Syntaxhervorhebung.

    ![Syntaxfehler anzeigen](../nodejs/media/tutorial-nodejs-syntax-checking.png)

    Die letzte Zeile dieser Meldung besagt, dass der JavaScript-Interpreter ein Komma erwartet (`,`).

1. Klicken Sie auf die Registerkarte **Fehlerliste**.

    Hier finden Sie die Warnung und die Beschreibung sowie den Dateinamen und die Zeilennummer.

    ![Fehlerliste anzeigen](../nodejs/media/tutorial-nodejs-error-list.png)

1. Korrigieren Sie den Code, indem Sie das Komma (`,`) vor `"data"` hinzufügen.

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

1. Klicken Sie in *index.js* im linken Bundsteg vor die folgende Codezeile, um einen Haltepunkt festzulegen:

    `res.render('index', { title: 'Express', "data": getData() });`

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

    ![Haltepunkt festlegen](../nodejs/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Wählen Sie das Debugziel in der Debug-Symbolleiste aus.

    ![Debugziel auswählen](../nodejs/media/tutorial-nodejs-deploy-target.png)

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**), um die Anwendung auszuführen.

    Der Debugger hält an dem Haltepunkt an, den Sie festlegen. Jetzt können Sie den Status Ihrer App überprüfen.

1. Zeigen Sie auf `getData`, um die Eigenschaften in einem DataTip anzuzeigen.

    ![Variablen überprüfen](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Drücken Sie **F5** (**Debuggen** > **Fortsetzen**), um den Vorgang fortzusetzen.

    Die App wird daraufhin in einem Browser geöffnet.

    Im Browserfenster wird im Titel „Express“ und im ersten Absatz „Welcome to Express“ (Willkommen bei Express) angezeigt.

1. Klicken Sie auf die Schaltflächen, um verschiedene Bilder anzuzeigen.

    ![Im Browser ausgeführte App](../nodejs/media/tutorial-nodejs-running-in-browser.png)

1. Schließen Sie den Webbrowser.

## <a name="optional-publish-to-azure-app-service"></a>(Optional) Veröffentlichen in Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

   ![Veröffentlichen in Azure App Service](../nodejs/media/tutorial-nodejs-publish-to-azure.png)

1. Klicken Sie auf **Microsoft Azure App Service**.

    Im Dialogfeld **App-Dienst** können Sie sich in Ihrem Azure-Konto anmelden und eine Verbindung mit vorhandenen Azure-Abonnements herstellen.

1. Führen Sie die verbleibenden Schritte aus, um ein Abonnement auszuwählen. Wählen Sie dann eine Ressourcengruppe aus, oder erstellen Sie eine. Wiederholen Sie dieselben Aktionen für einen App Service-Plan, und führen Sie die Schritte aus, wenn Sie zur Veröffentlichung in Azure aufgefordert werden. Eine ausführlichere Anleitung finden Sie unter [Publish to Azure Website using Web Deploy (Veröffentlichen auf einer Azure-Website mit Web Deploy)](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. Im Fenster **Ausgabe** wird der Fortschritt bei der Bereitstellung in Azure angezeigt.

    Bei erfolgreicher Bereitstellung wird Ihre App in einem Browser geöffnet, der in Azure App Service ausgeführt wird. Klicken Sie auf eine Schaltfläche, um ein Bild anzuzeigen.

   ![Die in Azure App Service ausgeführte App](../nodejs/media/tutorial-nodejs-running-in-azure.png)

Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erfahren, wie Sie mit Express eine Node.js-App erstellen und ausführen und wie Sie mit dem Debugger einen Haltepunkt festlegen.

> [!div class="nextstepaction"]
> [Node.js-Tools für Visual Studio](https://github.com/Microsoft/nodejstools)