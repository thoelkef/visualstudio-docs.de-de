---
title: 'Schnellstart: Verwenden von Visual Studio zum Erstellen einer ersten ASP.NET Core-Web-App | Microsoft-Dokumentation'
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: e87c46d1d78fafdc629a9f08e0bd7afacc1e1f3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App
Mithilfe dieser Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio, die fünf bis zehn Minuten Ihrer Zeit in Anspruch nehmen wird, können Sie eine einfache C#-ASP.NET Core-Web-Anwendung erstellen. Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.  

## <a name="create-a-project"></a>Erstellen eines Projekts
Zunächst müssen Sie ein Projekt für die ASP.NET Core-Webanwendung erstellen. Der Projekttyp enthält Vorlagendateien, die schon bevor Sie daran gearbeitet haben eine funktionsfähige Webanwendung darstellen.  

1. Öffnen Sie Visual Studio 2017.  

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt...**.  

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#**, und klicken Sie auf **.NET Core**. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Webanwendung** und anschließend auf **OK**.   

     Wenn Ihnen nicht die Projektvorlage **.NET Core** angezeigt wird, beenden Sie das Dialogfeld **Neues Projekt** und klicken Sie in der Menüleiste im oberen Bereich auf **Extras** > **Tools und Features abrufen...**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung**, und klicken Sie anschließend auf **Ändern**.  

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

1. Unter **Umgebung** und **Zeichenfolge** werden anschließend zwei wellenförmige Unterstreichungen angezeigt, da diese Typen nicht zu dem Bereich gehören. Öffnen Sie die Symbolleiste **Fehlerliste**. Dort werden dieselben Fehler aufgelistet. (Wenn Ihnen die Symbolleiste **Fehlerliste** nicht angezeigt wird, klicken Sie in der oberen Menüleiste auf **Ansicht** und dann auf **Fehlerliste**.)  

   ![Fehlerliste](../ide/media/quickstart-aspnet-errorlist.png)  

1. Platzieren Sie den Cursor im Editor-Fenster auf eine der Zeilen, die den Fehler enthalten, und klicken Sie anschließend am linken Rand auf die Glühbirne für „Schnelle Aktionen“. Klicken Sie im Dropdownmenü auf **using System;**, um diese Anweisung am Anfang der Datei hinzuzufügen und die Fehler zu beheben.  

## <a name="run-the-application"></a>Ausführen der Anwendung
1. Drücken Sie **STRG+F5**, um die Anwendung auszuführen und sie im Webbrowser zu öffnen.  

1. Klicken Sie im oberen Bereich der Website auf **Info**, um die Anweisungsmeldung abzurufen, die Sie in der `OnGet()`-Methode für die **Info**-Seite hinzugefügt haben.  

1. Schließen Sie den Webbrowser.  

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über die Visual Studio-IDE gelernt haben. Wenn Sie mehr über deren Funktionen erfahren möchten, können Sie gerne mit einem Tutorial im Inhaltsverzeichnis mit dem Abschnitt **Tutorials** fortfahren.  

## <a name="see-also"></a>Siehe auch   
[Getting Started with C# and Visual Basic using Visual Studio (Erste Schritte mit C# und Visual Basic mithilfe von Visual Studio)](getting-started-with-visual-csharp-and-visual-basic.md)
[Erste Schritte mit Razor-Seiten mit ASP.NET Core](/aspnet/core/tutorials/razor-pages/razor-pages-start)  