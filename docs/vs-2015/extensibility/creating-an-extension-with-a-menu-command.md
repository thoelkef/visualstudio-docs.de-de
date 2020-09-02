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
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572886"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine Erweiterung mit einem Menübefehl erstellen, der Notepad gestartet.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Erstellen eines Menübefehls  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen **firstmenucommand**. Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** " unter **Visual c#/Erweiterbarkeit**.  
  
2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **firstcommand**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in **FirstCommand.cs**.  
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
4. Öffnen Sie in der experimentellen Instanz das Fenster Extras  **/Erweiterungen und Updates** . Hier sollte die **firstmenucommand** -Erweiterung angezeigt werden. (Wenn Sie **Erweiterungen und Updates** in ihrer funktionierenden Instanz von Visual Studio öffnen, wird **firstmenucommand**nicht angezeigt.)  
  
     Wechseln Sie nun zum **Menü Extras in der experimentellen** Instanz. Der Befehl " **firstcommand aufrufen** " sollte angezeigt werden. An diesem Punkt wird nur ein Meldungs Feld mit dem Text "firstcommandpackage in firstmenucommand. firstcommand. MenuItemCallBack ()" angezeigt. Im nächsten Abschnitt erfahren Sie, wie Sie Notepad tatsächlich mit diesem Befehl starten.  
  
## <a name="changing-the-menu-command-handler"></a>Ändern des Menübefehls Handlers  
 Nun aktualisieren wir den Befehls Handler, um Notepad zu starten.  
  
1. Das Debuggen wird beendet, und Sie gelangen zurück zu ihrer funktionierenden Instanz von Visual Studio. Öffnen Sie die Datei FirstCommand.cs, und fügen Sie die folgende using-Anweisung hinzu:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Suchen Sie den privaten firstcommand-Konstruktor. An dieser Stelle wird der Befehl mit dem Befehls Dienst verknüpft, und der Befehls Handler wird angegeben. Ändern Sie den Namen des Befehls Handlers in startnotepad wie folgt:  
  
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
  
3. Entfernen Sie die MenuItemCallBack-Methode, und fügen Sie eine startnotepad-Methode hinzu, die nur den Notepad startet:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. Probieren Sie es jetzt aus. Wenn Sie mit dem Debuggen des Projekts beginnen und auf Extras **/firstcommand aufrufen**klicken, wird eine Instanz von Notepad angezeigt.  
  
     Sie können eine Instanz der- <xref:System.Diagnostics.Process> Klasse verwenden, um eine beliebige ausführbare Datei auszuführen, nicht nur Notepad. Probieren Sie es mit calc.exe aus, z. b..  
  
## <a name="cleaning-up-the-experimental-environment"></a>Bereinigen der experimentellen Umgebung  
 Wenn Sie mehrere Erweiterungen entwickeln oder nur Ergebnisse mit unterschiedlichen Versionen Ihres Erweiterungs Codes untersuchen, funktioniert Ihre experimentelle Umgebung möglicherweise nicht mehr so. In diesem Fall sollten Sie das Reset-Skript ausführen. Es heißt **Zurücksetzen der experimentellen Instanz von Visual Studio 2015**und wird als Teil des Visual Studio SDK ausgeliefert. Mit diesem Skript werden alle Verweise auf die Erweiterungen aus der experimentellen Umgebung entfernt, sodass Sie von Grund auf neu beginnen können.  
  
 Dieses Skript kann auf zwei Arten erreicht werden:  
  
1. Suchen Sie auf dem Desktop **die experimentelle Instanz von Visual Studio 2015 zurücksetzen**.  
  
2. Führen Sie die folgenden Befehle über die Befehlszeile aus:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Bereitstellen der Erweiterung  
 Nachdem Sie nun die Tool Erweiterung auf die gewünschte Weise ausgeführt haben, ist es an der Zeit, Sie mit Ihren Freunden und Kollegen zu teilen. Das ist ganz einfach, solange Visual Studio 2015 installiert ist. Sie müssen lediglich die von Ihnen erstellten. vsix-Datei an Sie senden. (Stellen Sie sicher, dass Sie im Releasemodus erstellt werden.)  
  
 Die vsix-Datei für diese Erweiterung finden Sie im Verzeichnis "firstmenucommand bin". Insbesondere, wenn Sie die Releasekonfiguration erstellt haben, befindet Sie sich in:  
  
 **\<code directory>\Firstmenucommand\firstmenucommand\bin\release\ firstmenucommand. vsix**  
  
 Um die Erweiterung zu installieren, muss Ihr Freund alle geöffneten Instanzen von Visual Studio schließen und dann auf die vsix-Datei doppelklicken, um das **VSIX-Installations**Programm aufzurufen. Die Dateien werden in das Verzeichnis **%LocalAppData%\microsoft\visualstudio\14.0\Extensions** kopiert.  
  
 Wenn Ihr Freund Visual Studio erneut öffnet, findet er die firstmenucommand-Erweiterung unter Extras **/Erweiterungen und Updates**. Er kann auch zu **Erweiterungen und Updates** wechseln, um die Erweiterung zu deinstallieren oder zu deaktivieren.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise haben Sie nur einen kleinen Teil der Möglichkeiten einer Visual Studio-Erweiterung gezeigt. Im folgenden finden Sie eine kurze Liste anderer (relativ einfacher) Dinge, die Sie mit Visual Studio-Erweiterungen machen können:  
  
1. Sie können mit einem einfachen Menübefehl viele weitere Aktionen ausführen:  
  
   1. Eigenes Symbol hinzufügen: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Ändern des Text des Menübefehls: Ändern des Texts [eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Hinzufügen einer Menü Verknüpfung zu einem Befehl: [Binden von Tastenkombinationen an Menü Elemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Fügen Sie verschiedene Arten von Befehlen, Menüs und Symbolleisten hinzu: [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)  
  
3. Hinzufügen von Tool Fenstern und Erweitern der integrierten Visual Studio-Tool Fenster: [erweitern und Anpassen von Tool Fenstern](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Hinzufügen von IntelliSense, Code Vorschlägen und anderen Features zu vorhandenen Code-Editoren: [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Hinzufügen von Optionen und Eigenschaften Seiten und Benutzereinstellungen zu ihrer Erweiterung: [Erweitern von Eigenschaften und des Eigenschaften Fensters](../extensibility/extending-properties-and-the-property-window.md) und [Erweitern von Benutzereinstellungen und-Optionen](../extensibility/extending-user-settings-and-options.md)  
  
   Andere Arten von Erweiterungen erfordern etwas mehr Arbeit, z. b. das Erstellen eines neuen Projekt Typs ([Erweitern von Projekten](../extensibility/extending-projects.md)), das Erstellen eines neuen Editor Typs ([Erstellen benutzerdefinierter Editoren und Designer](../extensibility/creating-custom-editors-and-designers.md)) oder das Implementieren der Erweiterung in einer isolierten Shell: [isolierte Visual Studio-Shell](../extensibility/visual-studio-isolated-shell.md)
