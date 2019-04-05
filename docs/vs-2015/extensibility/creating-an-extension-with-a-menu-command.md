---
title: Erstellen einer Erweiterung mit einem Menübefehl | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 644f763c64897eda4896c1431c815519dcc9b65f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957989"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht die Erstellung eine Erweiterung mit einem Menübefehl, der Editor wird gestartet.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Erstellen eines Menübefehls  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstMenuCommand**. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **FirstCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **FirstCommand.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Extras / Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstMenuCommand** Erweiterung. (Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio, nicht angezeigt **FirstMenuCommand**).  
  
     Lesen Sie jetzt die **Tools** Menü in der experimentellen Instanz. Daraufhin sollte **aufrufen FirstCommand** Befehl. An diesem Punkt wird nur ein Dialogfeld mit der Meldung "FirstCommandPackage in FirstMenuCommand.FirstCommand.MenuItemCallback()". Gewusst wie: Starten des Editors wirklich von diesem Befehl wird im nächsten Abschnitt sehen.  
  
## <a name="changing-the-menu-command-handler"></a>Ändern den Befehlshandler Menü  
 Jetzt aktualisieren wir den Befehlshandler zum Starten des Editors.  
  
1.  Debuggen beenden Sie, und wechseln Sie zurück zu Ihrer Arbeitsinstanz von Visual Studio. Öffnen Sie die FirstCommand.cs-Datei, und fügen Sie die folgenden using-Anweisung:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Suchen Sie den privaten FirstCommand-Konstruktor. Dies ist, in dem der Befehl ist mit dem Befehlsdienst eingebunden und die Befehlshandler angegeben ist. Ändern Sie den Namen der Befehlshandler, "startnotepad", wie folgt:  
  
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
  
3.  Entfernen Sie die MenuItemCallback-Methode, und fügen Sie eine "startnotepad"-Methode, die nur der Editor gestartet wird:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Probieren Sie es aus. Wenn Sie mit dem Debuggen des Projekts beginnen, und klicken Sie auf **Extras / aufrufen FirstCommand**, sollte eine Instanz des Editors angezeigt.  
  
     Können Sie eine Instanz von der <xref:System.Diagnostics.Process> Klasse Ausführen von ausführbaren Dateien, nicht nur Editor. Probieren Sie es mit calc.exe, z. B.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Bereinigen der experimentellen Umgebung  
 Wenn Sie mehrere Erweiterungen entwickeln, oder untersuchen nur Ergebnisse mit verschiedenen Versionen Ihres Codes für die Erweiterung, Ihre experimentelle Umgebung möglicherweise nicht mehr die Möglichkeit, wie, die Sie sollte. In diesem Fall sollten Sie das zurücksetzungsskript ausführen. Es heißt **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**, und es ist im Lieferumfang von Visual Studio SDK. Dieses Skript entfernt alle Verweise auf Ihre Erweiterungen aus der experimentellen Umgebung, sodass Sie von Grund auf neu beginnen können.  
  
 Sie können dieses Skript in eine von zwei Arten abrufen:  
  
1.  Suchen Sie auf dem Desktop **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**.  
  
2.  Führen Sie die folgenden Befehle über die Befehlszeile aus:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Bereitstellen der Erweiterungs  
 Nun, Sie die Tools-Erweiterung, die die gewünschte Weise ausführen haben, ist es Zeit, überlegen Sie sich mit Ihren Freunden und Kollegen freigeben. Das ist einfach, solange sie Visual Studio 2015 installiert haben. Müssen Sie lediglich die VSIX-Datei, die von Ihnen erstellte senden. (Achten Sie darauf erstellen im Releasemodus.)  
  
 Sie finden die VSIX-Datei für diese Erweiterung im FirstMenuCommand Bin-Verzeichnis. Insbesondere werden vorausgesetzt, dass Sie die Releasekonfiguration erstellt haben, es in:  
  
 **\<Verzeichnis "Code" > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Um die Erweiterung zu installieren, muss sich Ihr Freund, schließen Sie alle geöffneten Instanzen von Visual Studio, und doppelklicken Sie auf die VSIX-Datei, wird die **VSIX-Installationsprogramm**. Die Dateien werden kopiert, um die **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** Verzeichnis.  
  
 Wenn Ihr Freund Visual Studio dann erneut öffnet, findet er die FirstMenuCommand-Erweiterung in **Extras / Erweiterungen und Updates**. Er kann wechseln Sie zu **Erweiterungen und Updates** deinstallieren oder deaktivieren die Erweiterung zu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wurde gezeigt, nur einen kleinen Teil der Verwendungsmöglichkeiten mit Visual Studio-Erweiterung. Hier ist eine kurze Liste mit anderem (relativ einfach), die Sie mit Visual Studio-Erweiterungen ausführen können:  
  
1. Viele weitere Möglichkeiten mit einem einfachen Menübefehl möglich:  
  
   1.  Fügen Sie Ihr eigenes Symbol hinzu: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Ändern Sie den Text des Menübefehls: [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Fügen Sie eine Verknüpfung im Startmenü auf einen Befehl hinzu: [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Fügen Sie verschiedene Arten von Befehle, Menüs und Symbolleisten hinzu: [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)  
  
3. Fügen Sie Toolfenster, und erweitern Sie die integrierte Visual Studio-Toolfenster: [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Hinzufügen von IntelliSense Vorschläge für Code und andere Funktionen auf vorhandenen Code-Editoren: [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Fügen Sie die Seiten "Optionen" und "-Eigenschaft und die benutzereinstellungen zu Ihrer Erweiterung hinzu: [Erweitern von Eigenschaften und das Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md) und [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
   Andere Arten von Erweiterungen erfordern ein wenig mehr Arbeit, z. B. das Erstellen einer neuen Art von Projekt ([Erweitern von Projekten](../extensibility/extending-projects.md)), erstellen eine neue Art von Editor ([Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)), oder implementieren die Erweiterung in einer isolierten Shell ein: [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
