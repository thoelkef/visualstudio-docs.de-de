---
title: Erste Schritte mit Node.js in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 80822e4f323621a97beb453118d7e0836ae9ea92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Erste Schritte mit Node.js in Visual Studio
In diesem Tutorial für die Node.js-Entwicklung in Visual Studio werden wir eine einfache Node.js-Webanwendung erstellen, Code hinzufügen, einige Funktionen der IDE kennenlernen und die App ausführen. Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.  

## <a name="create-a-project"></a>Erstellen eines Projekts
Zunächst müssen Sie ein Projekt für die Node.js-Webanwendung erstellen.

1. Öffnen Sie Visual Studio 2017.  

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt...**.  

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **JavaScript**, und klicken Sie auf **Node.js**. Klicken Sie im mittleren Bereich auf **Azure Node.js Express 4-Basisanwendung** und anschließend auf **OK**.   

     Falls Sie die Projektvorlage **Azure Node.js Express 4-Basisanwendung** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**. 

    Visual Studio erstellt die neue Projektmappe und öffnet das Projekt. Die Projektdatei **app.js** wird im Editor (linker Bereich) geöffnet. Wenn Sie nicht mit Visual Studio-Projektmappen und -Projekten vertraut sind, lesen Sie den Artikel [Quickstart: Use Visual Studio to create your first Node.js app (Schnellstart: Erstellen der ersten Node.js-App mit Visual Studio)](../ide/quickstart-nodejs.md).

## <a name="add-some-code"></a>Hinzufügen von Code

1. Öffnen Sie im Projektmappen-Explorer (rechter Bereich) den Ordner „Views“ (Ansichten), und öffnen Sie „index.pug“.

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

1. Öffnen Sie im Ordner „routes“ die Datei „index.js.“.

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

1. Geben Sie nach `data` `: get` ein. IntelliSense zeigt Ihnen daraufhin die GetData-Funktion an. Klicken Sie auf `getData`.

    ![Verwendung von IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Wenn Sie das Komma (`,`) vor `"data"` entfernen, wird die Syntax im Ausdruck grün unterkringelt. Zeigen Sie auf die Syntaxhervorhebung.

    ![Syntaxfehler anzeigen](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    Die letzte Zeile dieser Meldung besagt, dass der JavaScript-Interpreter ein Komma erwartet (`,`).

1. Klicken Sie auf die Registerkarte **Fehlerliste**.

    Hier finden Sie die Warnung und die Beschreibung sowie den Dateinamen und die Zeilennummer.

    ![Fehlerliste anzeigen](../nodejs/media/tutorial-nodejs-error-list.png)

1. Korrigieren Sie den Code, indem Sie das Komma (`,`) vor `"data"` hinzufügen.

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

1. Klicken Sie in „index.js“ im linken Bundsteg vor die folgende Codezeile, um einen Haltepunkt festzulegen:

    `res.render('index', { title: 'Express', "data": getData() });`

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. 

    ![Haltepunkt festlegen](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Wählen Sie das Debugziel in der Debug-Symbolleiste aus.

    ![Debugziel auswählen](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Drücken Sie **STRG+F5**, um die Anwendung auszuführen.

    Der Debugger hält an dem Haltepunkt an, den Sie festlegen. Jetzt können Sie den Status Ihrer App überprüfen.

1. Zeigen Sie auf `getData`, um die Eigenschaften in einem DataTip anzuzeigen.

    ![Variablen überprüfen](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Drücken Sie **F5**, um fortzufahren.

    Die App wird daraufhin in einem Browser geöffnet.

    Im Browserfenster wird im Titel „Express“ und im ersten Absatz „Welcome to Express“ (Willkommen bei Express) angezeigt.

1. Klicken Sie auf die Schaltflächen, um verschiedene Bilder anzuzeigen.

1. Öffnen Sie das interaktive Node.js-Fenster, indem Sie **Ansicht > Weitere Fenster > Interaktives Node.js-Fenster** auswählen.

   ![Interaktives Node.js-Fenster öffnen](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    Das interaktive Fenster unterstützt jede Ihrer Aktionen im Code, einschließlich der Verwendung von `require()`-Anweisungen. Der Code im folgenden Screenshot definiert eine Variable und zeigt den Speicherort des Node.js-Interpreters.

   ![Interaktives Node.js-Fenster](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Schließen Sie den Webbrowser.  

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

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

- Weitere Informationen zu den [Node.js-Tools für Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Weitere Informationen zur [Visual Studio-IDE](../ide/visual-studio-ide.md)  