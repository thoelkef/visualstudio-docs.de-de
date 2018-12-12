---
title: Erstellen einer Erweiterung mit einem Menübefehl | Microsoft-Dokumentation
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
ms.openlocfilehash: 539ab866056b97f7054dda1843870dcfdd4379d9
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248136"
---
# <a name="create-an-extension-with-a-menu-command"></a>Erstellen Sie eine Erweiterung mit einem Menübefehl
Diese exemplarische Vorgehensweise veranschaulicht die Erstellung eine Erweiterung mit einem Menübefehl, der Editor wird gestartet.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-menu-command"></a>Erstellen eines Menübefehls  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstMenuCommand**. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** > **Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **FirstCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *FirstCommand.cs*.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Tools** > **Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstMenuCommand** Erweiterung. (Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio, nicht angezeigt **FirstMenuCommand**).  
  
     Lesen Sie jetzt die **Tools** Menü in der experimentellen Instanz. Daraufhin sollte **aufrufen FirstCommand** Befehl. An diesem Punkt nur daraufhin wird ein Dialogfeld mit der Meldung **FirstCommandPackage in FirstMenuCommand.FirstCommand.MenuItemCallback()**. Gewusst wie: Starten des Editors wirklich von diesem Befehl wird im nächsten Abschnitt sehen.  
  
## <a name="change-the-menu-command-handler"></a>Ändern Sie den Befehlshandler Menü  
 Jetzt aktualisieren wir den Befehlshandler zum Starten des Editors.  
  
1.  Debuggen beenden Sie, und wechseln Sie zurück zu Ihrer Arbeitsinstanz von Visual Studio. Öffnen der *FirstCommand.cs* Datei, und fügen Sie die folgenden using-Anweisung:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Suchen Sie den privaten FirstCommand-Konstruktor. Dies ist, in dem der Befehl ist mit dem Befehlsdienst eingebunden und die Befehlshandler angegeben ist. Ändern Sie den Namen der Befehlshandler, "startnotepad", wie folgt:  
  
    ```csharp  
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)  
    {  
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }  
    ```  
  
3.  Entfernen Sie die `MenuItemCallback` Methode und Hinzufügen einer `StartNotepad` -Methode die nur der Editor gestartet wird:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Probieren Sie es aus. Wenn Sie mit dem Debuggen des Projekts beginnen, und klicken Sie auf **Tools** > **aufrufen FirstCommand**, sollte eine Instanz des Editors angezeigt.  
  
     Können Sie eine Instanz von der <xref:System.Diagnostics.Process> Klasse Ausführen von ausführbaren Dateien, nicht nur Editor. Testen Sie es mit `calc.exe`, z. B.  
  
## <a name="clean-up-the-experimental-environment"></a>Bereinigen der experimentellen Umgebung  
 Wenn Sie mehrere Erweiterungen entwickeln, oder untersuchen nur Ergebnisse mit verschiedenen Versionen Ihres Codes für die Erweiterung, Ihre experimentelle Umgebung möglicherweise nicht mehr die Möglichkeit, wie, die Sie sollte. In diesem Fall sollten Sie das zurücksetzungsskript ausführen. Es heißt **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**, und es ist im Lieferumfang von Visual Studio SDK. Dieses Skript entfernt alle Verweise auf Ihre Erweiterungen aus der experimentellen Umgebung, sodass Sie von Grund auf neu beginnen können.  
  
 Sie können dieses Skript in eine von zwei Arten abrufen:  
  
1.  Suchen Sie auf dem Desktop **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**.  
  
2.  Führen Sie die folgenden Befehle über die Befehlszeile aus:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploy-your-extension"></a>Bereitstellen Sie Ihrer Erweiterung  
 Nun, Sie die Tools-Erweiterung, die die gewünschte Weise ausführen haben, ist es Zeit, überlegen Sie sich mit Ihren Freunden und Kollegen freigeben. Das ist einfach, solange sie Visual Studio 2015 installiert haben. Sie müssen lediglich senden ist die *VSIX* Datei, die Sie erstellt haben. (Achten Sie darauf erstellen im Releasemodus.)  
  
 Finden Sie die *VSIX* -Datei für diese Erweiterung in die *FirstMenuCommand* Verzeichnis "bin". Insbesondere werden vorausgesetzt, dass Sie die Releasekonfiguration erstellt haben, es in:  
  
 *\<Verzeichnis "Code" > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*  
  
 Um die Erweiterung zu installieren, muss sich Ihr Freund, schließen Sie alle geöffneten Instanzen von Visual Studio, und doppelklicken Sie auf die *VSIX* -Datei, die wird die **VSIX-Installationsprogramm**. Die Dateien werden kopiert, um die *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* Verzeichnis.  
  
 Wenn Ihr Freund Visual Studio dann erneut öffnet, findet er die FirstMenuCommand-Erweiterung in **Tools** > **Erweiterungen und Updates**. Er kann wechseln Sie zu **Erweiterungen und Updates** deinstallieren oder deaktivieren die Erweiterung zu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wurde gezeigt, nur einen kleinen Teil der Verwendungsmöglichkeiten mit Visual Studio-Erweiterung. Hier ist eine kurze Liste mit anderem (relativ einfach), die Sie mit Visual Studio-Erweiterungen ausführen können:  
  
1. Viele weitere Möglichkeiten mit einem einfachen Menübefehl möglich:  
  
   1.  Fügen Sie Ihr eigenes Symbol hinzu: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Ändern Sie den Text des Menübefehls: [Ändern Sie den Text eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Fügen Sie eine Verknüpfung im Startmenü auf einen Befehl hinzu: [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Fügen Sie verschiedene Arten von Befehle, Menüs und Symbolleisten hinzu: [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)  
  
3. Fügen Sie Toolfenster, und erweitern Sie die integrierte Visual Studio-Toolfenster: [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Hinzufügen von IntelliSense Vorschläge für Code und andere Funktionen auf vorhandenen Code-Editoren: [Erweitern Sie die Dienste, Editoren und Sprachen](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Fügen Sie die Seiten "Optionen" und "-Eigenschaft und die benutzereinstellungen zu Ihrer Erweiterung hinzu: [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md) und [benutzereinstellungen und Ooptions erweitern](../extensibility/extending-user-settings-and-options.md)  
  
   Andere Arten von Erweiterungen erfordern ein wenig mehr Arbeit, z. B. das Erstellen einer neuen Art von Projekt ([Projekte erweitern](../extensibility/extending-projects.md)), erstellen eine neue Art von Editor ([Erstellen benutzerdefinierter Editoren und Designer](../extensibility/creating-custom-editors-and-designers.md)), oder Implementieren Ihrer die Erweiterung in einer isolierten Shell: [Visual Studio isolated shell](../extensibility/visual-studio-isolated-shell.md)