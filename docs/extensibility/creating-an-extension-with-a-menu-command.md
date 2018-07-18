---
title: Erstellen eine Erweiterung mit einem Menübefehl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108153"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Erstellen eine Erweiterung mit einem Menübefehl
In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine Erweiterung mit einem Menübefehl zu erstellen, der Editor startet.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Erstellen eines Menübefehls  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstMenuCommand**. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **FirstCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **FirstCommand.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Extras / Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstMenuCommand** hier Erweiterung. (Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeit Instanz von Visual Studio, werden Sie nicht angezeigt **FirstMenuCommand**).  
  
     Lesen Sie jetzt die **Tools** Menü in der experimentellen Instanz. Daraufhin sollte **FirstCommand Aufrufen** Befehl. Zu diesem Zeitpunkt wird nur ein Dialogfeld mit der Meldung "FirstCommandPackage in FirstMenuCommand.FirstCommand.MenuItemCallback()". Wir sehen, dass tatsächlich Starten der Editor dieses Befehls im nächsten Abschnitt.  
  
## <a name="changing-the-menu-command-handler"></a>Ändern die Handler für das Menü-Befehl  
 Jetzt aktualisieren wir die Befehlshandler um Editor zu starten.  
  
1.  Beenden Sie des Debuggens, und wechseln Sie zurück zu Ihrer Arbeit Instanz von Visual Studio. Öffnen Sie die Datei FirstCommand.cs, und fügen Sie die folgende Anweisung:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Suchen Sie den privaten FirstCommand-Konstruktor. Dies ist, in dem der Befehl ist mit dem Befehl Dienst verknüpft und Befehlshandler angegeben ist. Ändern Sie den Namen der Befehlshandler in StartNotepad, wie folgt:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Entfernen Sie die MenuItemCallback-Methode, und fügen Sie eine StartNotepad-Methode, die nur der Editor gestartet wird:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Probieren Sie es aus. Wenn Sie Debuggen des Projekts starten, und klicken Sie auf **Extras / aufrufen FirstCommand**, sehen Sie eine Instanz von Editor aufgerufen werden.  
  
     Können Sie eine Instanz von der <xref:System.Diagnostics.Process> Klasse zum Ausführen von ausführbaren Dateien, nicht nur in Editor. Versuchen Sie es mit calc.exe, z. B.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Bereinigen die experimentelle Umgebung  
 Wenn Sie mehrere Erweiterungen entwickeln, oder untersuchen nur Ergebnisse mit verschiedenen Versionen des Codes Erweiterung, die experimentelle Umgebung möglicherweise nicht funktionsfähig mehr, die es sollte, wie. In diesem Fall sollten Sie das Zurücksetzen-Skript ausführen. Es heißt **Zurücksetzen der experimentellen Instanz von Visual Studio 2015**, und es als Teil der Visual Studio-SDK geliefert wird. Dieses Skript entfernt alle Verweise auf die Erweiterungen aus der experimentellen Umgebung aus, damit Sie von Grund auf neu starten können.  
  
 Sie können dieses Skript auf zwei Arten abrufen:  
  
1.  Suchen Sie auf dem Desktop **Zurücksetzen der experimentellen Instanz von Visual Studio 2015**.  
  
2.  Führen Sie über die Befehlszeile Folgendes ein:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Bereitstellen der Erweiterungs  
 Nun, Sie die toolerweiterung, die die gewünschte Weise ausgeführt haben, ist es Zeit, die zu Ihren Freunden und Ihrer Kollegen freigeben. Also einfach, solange sie Visual Studio 2015 installiert haben. Alles, was Sie tun müssen ist, senden sie die VSIX-Datei, die Sie erstellt haben. (Achten Sie darauf, im Releasemodus erstellen.)  
  
 Sie können für diese Erweiterung die VSIX-Datei im Verzeichnis "bin" FirstMenuCommand finden. Insbesondere wird angenommen, Sie haben die Release-Konfiguration erstellt, es:  
  
 **\<Code (Verzeichnis) > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Um die Erweiterung zu installieren, muss Ihre "Friend" Schließen Sie alle geöffneten Instanzen von Visual Studio, und doppelklicken Sie auf die VSIX-Datei wird die **VSIX-Installationsprogramm**. Die Dateien werden kopiert, um die **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** Verzeichnis.  
  
 Wenn Ihre "Friend" Einrichten von Visual Studio bringt, anwendungsverwaltungsoptionen er die FirstMenuCommand-Erweiterung in **Extras / Erweiterungen und Updates**. Er kann an mich bei **Erweiterungen und Updates** deinstallieren oder deaktivieren die Erweiterung zu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise haben Sie nur einen kleinen Teil der Verwendungsmöglichkeiten mit einer Visual Studio-Erweiterung gezeigt. Hier ist eine kurze Liste mit anderem (relativ einfach), die Sie mit Visual Studio-Erweiterungen ausführen können:  
  
1.  Sie können viele weitere Möglichkeiten mit einen einfachen Befehl ausführen:  
  
    1.  Eigene Symbol "hinzufügen": [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Ändern Sie den Text des Menübefehls: [ändern den Text eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Tastenkombination für einen Befehl hinzufügen: [Binden von Tastenkombinationen für Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Verschiedene Arten von Befehle, Menüs und Symbolleisten hinzufügen: [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)  
  
3.  Toolfenster hinzufügen und erweitern Sie die integrierte Visual Studio-Toolfenster: [Extending und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Hinzufügen von IntelliSense Code Vorschläge und weitere Funktionen, um vorhandene-Codeeditoren: [Erweiterung des Editors und des Language-Dienste](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Hinzufügen von Seiten "Optionen" und "-Eigenschaft und die benutzereinstellungen der Durchwahl: [Erweitern von Eigenschaften und des Fensters Eigenschaften](../extensibility/extending-properties-and-the-property-window.md) und [Benutzereinstellungen erweitern und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
 Andere Arten von Erweiterungen erfordern ein wenig mehr Arbeit, z. B. das Erstellen des Projekts eines neuen Typs ([Erweitern von Projekten](../extensibility/extending-projects.md)), erstellen einen neuen Typ-Editor ([Erstellen benutzerdefinierter Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)), oder implementieren die Erweiterung in einer isolierten Shell: [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)