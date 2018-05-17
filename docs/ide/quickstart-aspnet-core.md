---
title: Verwenden von Visual Studio zum Erstellen einer ASP.NET Core-Web-App in C#
description: Dieser Artikel enthält eine ausführliche Anleitung zum Erstellen einer ASP.NET Core-Web-App mit C# in Visual Studio.
ms.custom: mvc
ms.date: 10/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1b74f47201c706cbb4fe4a4f0eca647b350d9a72
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App

Mithilfe dieser Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio, die fünf bis zehn Minuten Ihrer Zeit in Anspruch nehmen wird, können Sie eine einfache C#-ASP.NET Core-Web-Anwendung erstellen.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die ASP.NET Core-Webanwendung erstellen. Der Projekttyp enthält Vorlagendateien, die schon bevor Sie daran gearbeitet haben eine funktionsfähige Webanwendung darstellen.

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#**, und klicken Sie auf **.NET Core**. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Webanwendung** und anschließend auf **OK**.

     Falls Sie die Projektvorlagenkategorie **.NET Core** nicht finden, klicken Sie im linken Bereich auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung**, und klicken Sie anschließend auf **Ändern**.

     ![ASP.NET-Workload in VS-Installer](../ide/media/quickstart-aspnet-workload.png)

1. Klicken Sie im oberen Dropdownmenü des Dialogfelds **Neue ASP.NET Core-Webanwendung** auf **ASP.NET Core 2.0**. (Wenn **ASP.NET Core 2.0** nicht in der Liste angezeigt wird, installieren Sie es über den **Download**-Link, der in einer gelben Leiste im oberen Bereich des Dialogfelds angezeigt werden sollte.) Klicken Sie auf **OK**.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Durchsuchen der IDE

1. Erweitern Sie in der Symbolleiste des **Projektmappen-Explorers** den Ordner **Pages** (Seiten), und klicken Sie anschließend auf **About.cshtml**, um sie im Editor zu öffnen. Diese Datei ist einer Seite mit der Bezeichnung **Info** in der Webanwendung zugeordnet.

1. Klicken Sie im Editor auf `AboutModel`, und drücken Sie dann **F12**, oder klicken Sie im Kontextmenü (Rechtsklick) auf **Gehe zu Definition**. Über diesen Befehl gelangen Sie zu der Definition der `AboutModel`-C#-Klasse.

   ![Kontextmenü „Gehe zu Definition“](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Als Nächstes werden die `using`-Anweisungen im oberen Bereich der Datei über eine einfache Verknüpfung bereinigt. Klicken Sie auf eine der ausgegrauten Anweisungen, damit die Glühbirne für [Schnelle Aktionen](../ide/quick-actions.md) unter dem Caretzeichen oder auf dem linken Rand angezeigt wird. Klicken Sie zunächst auf die Glühbirne und anschließend auf **Nicht benötigte Using-Direktiven entfernen**.

     Dann werden nicht benötigte Using-Direktiven aus der Datei gelöscht.

1. Ändern Sie in der `OnGet()`-Methode den Text in den folgenden Code:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Unter **Umgebung** und **Zeichenfolge** werden anschließend zwei wellenförmige Unterstreichungen angezeigt, da diese Typen nicht zu dem Bereich gehören. Öffnen Sie die Symbolleiste **Fehlerliste**. Dort werden dieselben Fehler aufgelistet. (Wenn Ihnen die Symbolleiste **Fehlerliste** nicht angezeigt wird, klicken Sie in der oberen Menüleiste auf **Ansicht** > **Fehlerliste**.)

   ![Fehlerliste](../ide/media/quickstart-aspnet-errorlist.png)

1. Platzieren Sie den Cursor im Editor-Fenster auf eine der Zeilen, die den Fehler enthalten, und klicken Sie anschließend am linken Rand auf die Glühbirne für „Schnelle Aktionen“. Klicken Sie im Dropdownmenü auf **using System;**, um diese Anweisung am Anfang der Datei hinzuzufügen und die Fehler zu beheben.

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Drücken Sie **STRG**+**F5**, um die Anwendung auszuführen und sie im Webbrowser zu öffnen.

1. Klicken Sie im oberen Bereich der Website auf **Info**, um die Anweisungsmeldung abzurufen, die Sie in der `OnGet()`-Methode für die **Info**-Seite hinzugefügt haben.

1. Schließen Sie den Webbrowser.

> [!NOTE]
> Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver "IIS Express" hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über die Visual Studio-IDE gelernt haben. Wenn Sie mehr über deren Funktionen erfahren möchten, können Sie gerne mit einem Tutorial im Inhaltsverzeichnis mit dem Abschnitt **Tutorials** fortfahren.

## <a name="next-steps"></a>Nächste Schritte
Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE gelernt haben. Fahren Sie für weitere Informationen mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Erste Schritte mit C# und ASP.NET in Visual Studio](tutorial-csharp-aspnet-core.md)
