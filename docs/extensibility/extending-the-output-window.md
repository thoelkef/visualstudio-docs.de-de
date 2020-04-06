---
title: Erweitern des Ausgabefensters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711642"
---
# <a name="extend-the-output-window"></a>Erweitern des Ausgabefensters
Das **Ausgabefenster** ist ein Satz von Lese-/Schreibtextbereichen. Visual Studio verfügt über die folgenden integrierten Bereiche: **Build**, in dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte Nachrichten zu Builds kommunizieren, und **Allgemein**, in dem Nachrichten über die IDE kommuniziert werden. Projekte erhalten automatisch über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellenmethoden einen Verweis auf den **Buildbereich,** und <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Visual Studio bietet über den Dienst direkten Zugriff auf den **Bereich Allgemein.** Zusätzlich zu den integrierten Bereichen können Sie eigene benutzerdefinierte Bereiche erstellen und verwalten.

 Sie können das **Ausgabefenster** <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> direkt <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> über die und Schnittstellen steuern. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle, die vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> Dienst angeboten wird, definiert Methoden zum Erstellen, Abrufen und Zerstören von **Ausgabefensterfenstern.** Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstelle definiert Methoden zum Anzeigen von Bereichen, Ausblenden von Bereichen und Bearbeiten ihres Textes. Eine alternative Möglichkeit zum Steuern des <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> **Ausgabefensters** ist die und Objekte im Visual Studio Automation-Objektmodell. Diese Objekte kapseln fast die gesamte <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Funktionalität <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> der und Schnittstellen. Darüber hinaus <xref:EnvDTE.OutputWindow> fügen <xref:EnvDTE.OutputWindowPane> die und-Objekte einige Funktionen auf höherer Ebene hinzu, um das Aufzählen der **Ausgabefensterbereiche** und das Abrufen von Text aus den Bereichen zu vereinfachen.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Erstellen einer Erweiterung, die den Ausgabebereich verwendet
 Sie können eine Erweiterung erstellen, die verschiedene Aspekte des Ausgabebereichs ausführt.

1. Erstellen Sie ein `TestOutput` VSIX-Projekt mit dem Namen mit einem Menübefehl mit dem Namen **TestOutput**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Fügen Sie die folgenden Verweise hinzu:

    1. EnvDTE

    2. EnvDTE80

3. Fügen Sie in *TestOutput.cs*die folgende Usingsanweisung hinzu:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. Löschen *Sie*in `ShowMessageBox` TestOutput.cs die Methode. Fügen Sie den folgenden Methodenstub hinzu:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. Ändern Sie im TestOutput-Konstruktor den Befehlshandler in OutputCommandHandler. Hier ist der Teil, der die Befehle hinzufügt:

    ```csharp
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    if (commandService != null)
    {
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
        EventHandler eventHandler = OutputCommandHandler;
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

6. Die folgenden Abschnitte haben verschiedene Methoden, die verschiedene Methoden für den Umgang mit dem Ausgabebereich aufzeigen. Sie können diese Methoden als `OutputCommandHandler()` Text der Methode aufrufen. Der folgende Code fügt `CreatePane()` z. B. die im nächsten Abschnitt angegebene Methode hinzu.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Erstellen eines Ausgabefensters mit IVsOutputWindow
 In diesem Beispiel wird gezeigt, wie Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> mithilfe der Schnittstelle einen neuen **Ausgabefensterbereich** erstellen.

```csharp
void CreatePane(Guid paneGuid, string title,
    bool visible, bool clearWithSolution)
{
    IVsOutputWindow output =
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));
    IVsOutputWindowPane pane;

    // Create a new pane.
    output.CreatePane(
        ref paneGuid,
        title,
        Convert.ToInt32(visible),
        Convert.ToInt32(clearWithSolution));

    // Retrieve the new pane.
    output.GetPane(ref paneGuid, out pane);

     pane.OutputString("This is the Created Pane \n");
}
```

 Wenn Sie diese Methode der im vorherigen Abschnitt angegebenen Erweiterung hinzufügen, sollten Sie beim Klicken auf den Befehl **TestOutput aufrufen** das **Ausgabefenster** mit einer Kopfzeile anzeigen sehen, die **Ausgabe anzeigen aus: CreatedPane** und den **Wörtern Dies ist der erstellte Bereich** im Bereich selbst.

## <a name="create-an-output-window-with-outputwindow"></a>Erstellen eines Ausgabefensters mit OutputWindow
 In diesem Beispiel wird gezeigt, wie <xref:EnvDTE.OutputWindow> Sie mithilfe des Objekts einen **Ausgabefensterbereich** erstellen.

```csharp
void CreatePane(string title)
{
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;

    try
    {
        // If the pane exists already, write to it.
        panes.Item(title);
    }
    catch (ArgumentException)
    {
        // Create a new pane and write to it.
        panes.Add(title);
    }
}
```

 Obwohl <xref:EnvDTE.OutputWindowPanes> Sie mit der Auflistung einen **Ausgabefensterbereich** anhand ihres Titels abrufen können, sind Bereichstitel nicht garantiert eindeutig. Wenn Sie die Eindeutigkeit eines Titels bezweifeln, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den richtigen Bereich über seine GUID abzurufen.

 Wenn Sie diese Methode der im vorherigen Abschnitt angegebenen Erweiterung hinzufügen, sollten Sie beim Klicken auf den Befehl **TestOutput aufrufen** das Ausgabefenster mit einer Kopfzeile anzeigen sehen, die **Ausgabe anzeigen aus: DTEPane** und den Wörtern **Hinzugefügter DTE-Bereich** im Bereich selbst angibt.

## <a name="delete-an-output-window"></a>Löschen eines Ausgabefensters
 In diesem Beispiel wird gezeigt, wie Sie einen **Ausgabefensterbereich** löschen.

```csharp
void DeletePane(Guid paneGuid)
{
    IVsOutputWindow output =
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));

    IVsOutputWindowPane pane;
    output.GetPane(ref paneGuid, out pane);

    if (pane == null)
    {
        CreatePane(paneGuid, "New Pane\n", true, true);
    }
     else
    {
        output.DeletePane(ref paneGuid);
    }
}
```

 Wenn Sie diese Methode der im vorherigen Abschnitt angegebenen Erweiterung hinzufügen, sollten Sie beim Klicken auf den Befehl **TestOutput aufrufen** das Ausgabefenster mit einer Kopfzeile anzeigen sehen, die **Ausgabe anzeigen aus: Neuer Bereich** und den Wörtern **"Erstellter Bereich hinzugefügt"** im Bereich selbst anzeigt. Wenn Sie erneut auf den Befehl **TestOutput aufrufen** klicken, wird der Bereich gelöscht.

## <a name="get-the-general-pane-of-the-output-window"></a>Abrufen des Fensters Allgemein des Ausgabefensters
 In diesem Beispiel wird gezeigt, wie Sie den integrierten **Bereich Allgemein** des **Ausgabefensters** abrufen.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Wenn Sie diese Methode der im vorherigen Abschnitt angegebenen Erweiterung hinzufügen, sollten Sie beim Klicken auf den Befehl **TestOutput aufrufen** sehen, dass im **Ausgabefenster** die Wörter **"Erster Allgemein"** im Bereich angezeigt werden.

## <a name="get-the-build-pane-of-the-output-window"></a>Abrufen des Buildfensters des Ausgabefensters
 In diesem Beispiel wird gezeigt, wie Sie den **Buildbereich** finden und darauf schreiben. Da der **Buildbereich** nicht standardmäßig aktiviert ist, wird er ebenfalls aktiviert.

```csharp
void OutputTaskItemStringExExample(string buildMessage)
{
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));

    EnvDTE.OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;
    foreach (EnvDTE.OutputWindowPane pane in panes)
        {
            if (pane.Name.Contains("Build"))
            {
                pane.OutputString(buildMessage + "\n");
                pane.Activate();
                return;
             }
        }
}
```
