---
title: Erstellen einer Erweiterung mit einem Menübefehl | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739561"
---
# <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine Erweiterung mit einem Menübefehl erstellen, der Notepad startet.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Erstellen eines Menübefehls

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstMenuCommand**. Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehlselementvorlage mit dem Namen **FirstCommand**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *FirstCommand.cs*.

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

    Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Öffnen Sie in der experimentellen Instanz das Fenster **Tools** > **Extensions and Updates.** Sie sollten die **FirstMenuCommand-Erweiterung** hier sehen. (Wenn Sie **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio öffnen, wird **FirstMenuCommand**nicht angezeigt.

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie in der experimentellen Instanz das Fenster **Erweiterungen** > **verwalten.** Sie sollten die **FirstMenuCommand-Erweiterung** hier sehen. (Wenn Sie **Erweiterungen** verwalten in Ihrer Arbeitsinstanz von Visual Studio öffnen, wird **FirstMenuCommand**nicht angezeigt.

::: moniker-end

Wechseln Sie nun zum Menü **Extras** in der experimentellen Instanz. Sie sollten den Befehl **FirstCommand aufrufen** sehen. An diesem Punkt wird der Befehl ein Meldungsfeld mit der Meldung **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()** angezeigt. Wie Sie Notepad tatsächlich mit diesem Befehl starten, erfahren Sie im nächsten Abschnitt.

## <a name="change-the-menu-command-handler"></a>Ändern des Menübefehlshandlers

Aktualisieren wir nun den Befehlshandler, um Notepad zu starten.

1. Beenden Sie das Debuggen, und kehren Sie zu Ihrer funktionierenden Instanz von Visual Studio zurück. Öffnen Sie die *FirstCommand.cs* Datei, und fügen Sie die folgende Usinger Anweisung hinzu:

    ```csharp
    using System.Diagnostics;
    ```

2. Suchen Sie den privaten FirstCommand-Konstruktor. Hier wird der Befehl an den Befehlsdienst angeschlossen und der Befehlshandler angegeben. Ändern Sie den Namen des Befehlshandlers wie folgt in StartNotepad:

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

3. Entfernen `MenuItemCallback` Sie die `StartNotepad` Methode, und fügen Sie eine Methode hinzu, mit der Notepad gestartet wird:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Probieren Sie es jetzt aus. Wenn Sie mit dem Debuggen des Projekts beginnen und auf **Extras** > **Invoke FirstCommand**klicken, sollte eine Instanz von Notepad angezeigt werden.

    Sie können eine Instanz <xref:System.Diagnostics.Process> der Klasse verwenden, um eine ausführbare Datei auszuführen, nicht nur Notepad. Probieren Sie `calc.exe`es z. B. mit.

## <a name="clean-up-the-experimental-environment"></a>Bereinigen der experimentellen Umgebung

Wenn Sie mehrere Erweiterungen entwickeln oder nur Ergebnisse mit verschiedenen Versionen Ihres Erweiterungscodes untersuchen, funktioniert Ihre experimentelle Umgebung möglicherweise nicht mehr so, wie sie sollte. In diesem Fall sollten Sie das Reset-Skript ausführen. Es heißt **Reset the Visual Studio Experimental Instance**, und wird als Teil des Visual Studio SDK ausgeliefert. Dieses Skript entfernt alle Verweise auf Ihre Erweiterungen aus der experimentellen Umgebung, sodass Sie von Grund auf neu beginnen können.

Sie können auf zwei Arten auf dieses Skript zugelangen:

1. Suchen Sie auf dem Desktop nach **Zurücksetzen der Visual Studio Experimental Instance**.

2. Führen Sie die folgenden Befehle über die Befehlszeile aus:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Stellen Sie Ihre Erweiterung bereit

Jetzt, da Ihre Tool-Erweiterung so läuft, wie Sie wollen, ist es an der Zeit, darüber nachzudenken, sie mit Ihren Freunden und Kollegen zu teilen. Das ist einfach, solange Visual Studio 2015 installiert ist. Alles, was Sie tun müssen, ist ihnen die *.vsix-Datei* zu senden, die Sie erstellt haben. (Stellen Sie sicher, dass Sie es im Release-Modus erstellen.)

Sie finden die *.vsix-Datei* für diese Erweiterung im *Verzeichnis FirstMenuCommand* bin. Wenn Sie die Release-Konfiguration erstellt haben, wird sie sich insbesondere in folgenden Informationen aufstellen:

*\<Code-Verzeichnis>-FirstMenuCommand-FirstMenuCommand-Bin-Release-FirstMenuCommand.vsix*

Um die Erweiterung zu installieren, muss Ihr Freund alle geöffneten Instanzen von Visual Studio schließen und dann auf die *.vsix-Datei* doppelklicken, die den **VSIX Installer aufruft.** Die Dateien werden in das Verzeichnis *%LocalAppData%-Microsoft-VisualStudio->-Erweiterungen\<* kopiert.

Wenn Ihr Freund Visual Studio erneut aufruft, findet er die FirstMenuCommand-Erweiterung in **Tools** > **Extensions and Updates**. Sie können zu **Erweiterungen und Updates** gehen, um die Erweiterung zu deinstallieren oder zu deaktivieren.

## <a name="next-steps"></a>Nächste Schritte

In dieser exemplarischen Vorgehensweise wurde gezeigt, dass Sie nur einen kleinen Teil dessen, was Sie mit einer Visual Studio-Erweiterung tun können, haben. Hier ist eine kurze Liste anderer (relativ einfacher) Dinge, die Sie mit Visual Studio-Erweiterungen tun können:

1. Sie können viele weitere Dinge mit einem einfachen Menübefehl tun:

   1. Fügen Sie Ihr eigenes Symbol hinzu: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)

   2. Text des Menübefehls ändern: [Ändern des Textes eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Hinzufügen einer Menüverknüpfung zu einem Befehl: [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Hinzufügen verschiedener Arten von Befehlen, Menüs und Symbolleisten: [Menüs und Befehle erweitern](../extensibility/extending-menus-and-commands.md)

3. Hinzufügen von Toolfenstern und Erweitern der integrierten Visual Studio-Toolfenster: [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)

4. Hinzufügen von IntelliSense, Codevorschlägen und anderen Funktionen zu vorhandenen Code-Editoren: [Erweitern sie den Editor und die Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)

5. Hinzufügen von Optionen und Eigenschaftenseiten und Benutzereinstellungen zu Ihrer Erweiterung: Erweitern von [Eigenschaften und dem Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md) und Erweitern von [Benutzereinstellungen und -optionen](../extensibility/extending-user-settings-and-options.md)

   Andere Arten von Erweiterungen erfordern etwas mehr Arbeit, z. B. das Erstellen eines neuen Projekttyps ([Projekt erweitern](../extensibility/extending-projects.md)), Erstellen eines neuen Editortyps ([Erstellen benutzerdefinierter Editoren und Designer](../extensibility/creating-custom-editors-and-designers.md)) oder Implementieren der Erweiterung in einer isolierten Shell: Visual [Studio-isolierte Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
