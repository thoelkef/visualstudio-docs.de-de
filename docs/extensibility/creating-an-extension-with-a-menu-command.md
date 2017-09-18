---
title: "Erstellen eine Erweiterung mit einem Men&#252;befehl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schreiben Sie ein vspackage"
  - "VSPackage"
  - "Lernprogramme"
  - "Visual Studio-Paket"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 56
---
# Erstellen eine Erweiterung mit einem Men&#252;befehl
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie eine Erweiterung mit einem Menübefehl erstellt, die Editor startet.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines Menübefehls  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **FirstMenuCommand**. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **FirstCommand**. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **FirstCommand.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den  **Extras \/ Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstMenuCommand** Erweiterung. \(Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio, nicht angezeigt **FirstMenuCommand**\).  
  
     Lesen Sie jetzt den **Tools** Menü in der experimentellen Instanz. Daraufhin sollte **aufrufen FirstCommand** Befehl. An diesem Punkt wird nur ein Meldungsfeld mit dem Text "FirstCommandPackage in FirstMenuCommand.FirstCommand.MenuItemCallback\(\)". Wir sehen, wie den Editor tatsächlich von diesem Befehl im nächsten Abschnitt zu starten.  
  
## Ändern den Befehlshandler Menü  
 Jetzt aktualisieren wir den Befehlshandler, um den Editor zu starten.  
  
1.  Beenden Sie das Debuggen, und wechseln Sie zurück zu Ihrer Arbeitsinstanz von Visual Studio. Öffnen Sie die Datei FirstCommand.cs, und fügen Sie die folgende using\-Anweisung:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  Suchen Sie den privaten FirstCommand\-Konstruktor. Hier wird der Befehl mit dem Befehl Dienst verknüpft ist und der Befehlshandler angegeben ist. Ändern Sie den Namen der Befehlshandler in "startnotepad", wie folgt:  
  
    ```c#  
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
  
3.  Entfernen Sie die MenuItemCallback\-Methode, und fügen Sie eine StartNotepad\-Methode, die nur Editor gestartet werden kann:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Probieren Sie es aus. Wenn Sie mit dem Debuggen des Projekts beginnen, und klicken Sie auf **Extras \/ aufrufen FirstCommand**, sollte eine Instanz von Editor gestartet.  
  
     Können Sie eine Instanz der <xref:System.Diagnostics.Process> \-Klasse zum Ausführen von ausführbaren Dateien, nicht nur Editor. Versuchen Sie es mit calc.exe, z. B..  
  
## Bereinigen von der experimentellen Umgebung  
 Wenn Sie mehrere Erweiterungen entwickeln, oder nur Ergebnisse mit unterschiedlichen Versionen für den Code untersuchen, eventuell wie gewünscht funktioniert Ihre experimentelle Umgebung nicht. In diesem Fall sollten Sie das zurücksetzungsskript ausführen. Es heißt **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**, und es ist im Lieferumfang von Visual Studio SDK. Dieses Skript entfernt alle Verweise auf Ihre Erweiterungen aus der experimentellen Umgebung, sodass Sie von Grund auf neu beginnen können.  
  
 Sie können dieses Skript in eine von zwei Arten abrufen:  
  
1.  Suchen Sie auf dem Desktop **Zurücksetzen der experimentellen Instanz der Visual Studio 2015**.  
  
2.  Führen Sie über die Befehlszeile Folgendes ein:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## Bereitstellen der Erweiterungs  
 Nun, Sie die toolerweiterung, die die gewünschte Weise ausführen haben, ist es Zeit, darüber nachzudenken, Freunden und Kollegen freigeben. Das ist einfach, solange sie Visual Studio 2015 installiert haben. Sie müssen lediglich lediglich senden sie die VSIX\-Datei, die Sie erstellt haben. \(Achten Sie darauf im Releasemodus erstellen.\)  
  
 Sie finden die VSIX\-Datei für diese Erweiterung im FirstMenuCommand Bin\-Verzeichnis. Insbesondere werden vorausgesetzt, dass Sie die Releasekonfiguration erstellt haben, es in:  
  
 **\< Verzeichnis \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 Um die Erweiterung zu installieren, muss Ihr Freund, schließen Sie alle geöffneten Instanzen von Visual Studio, und doppelklicken Sie auf die VSIX\-Datei zeigt die **VSIX\-Installationsprogramm**. Die Dateien werden kopiert, um die **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** Verzeichnis.  
  
 Wenn Ihr Freund Visual Studio erneut angezeigt werden, findet er die FirstMenuCommand\-Erweiterung in **Extras \/ Erweiterungen und Updates**. Er kann finden Sie unter **Erweiterungen und Updates** deinstallieren oder die Erweiterung zu deaktivieren.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wurde gezeigt, nur einen kleinen Teil mit Visual Studio\-Erweiterung möglich. Hier wird eine kurze Liste mit anderem \(relativ einfach\), die Sie mit Visual Studio\-Erweiterungen durchführen können:  
  
1.  Sie können viele weitere Dinge mit einen einfachen Befehl ausführen:  
  
    1.  Fügen Sie Ihr eigenes Symbol: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Ändern Sie den Text des Menübefehls: [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Fügen Sie eine Tastenkombination im Menü auf einen Befehl hinzu: [Bindung\-Tastenkombinationen für Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Fügen Sie verschiedene Arten von Befehle, Menüs und Symbolleisten: [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)  
  
3.  Hinzufügen von Toolfenstern, und erweitern Sie die integrierte Visual Studio\-Toolfenster: [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Fügen Sie IntelliSense, Code Vorschläge und anderen Funktionen auf vorhandenen Code\-Editoren: [Erweitern der\-Editor und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Die Erweiterung oder Optionen auf den Eigenschaftenseiten und Einstellungen hinzufügen: [Erweitern von Eigenschaften und das Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md) und [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
 Andere Arten von Erweiterungen erfordern ein wenig mehr Aufwand, wie z. B. die Erstellung eines neuen Projekts \([Erweitern von Projekten](../extensibility/extending-projects.md)\), erstellen einen neuen Typ\-Editor \([Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)\), oder implementieren die Erweiterung in eine isolierte Shell: [Visual Studio Shell Isolated](../extensibility/visual-studio-isolated-shell.md)