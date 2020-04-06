---
title: Erweitern der Statusleiste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711544"
---
# <a name="extend-the-status-bar"></a>Erweitern der Statusleiste
Sie können die Visual Studio-Statusleiste am unteren Rand der IDE verwenden, um Informationen anzuzeigen.

 Wenn Sie die Statusleiste erweitern, können Sie Informationen und Benutzeroberfläche in vier Regionen anzeigen: dem Feedbackbereich, der Fortschrittsleiste, dem Animationsbereich und dem Designerbereich. Im Feedbackbereich können Sie Text anzeigen und den angezeigten Text hervorheben. Die Fortschrittsleiste zeigt den inkrementellen Fortschritt für Vorgänge mit kurzer Ausführungszeit an, z. B. das Speichern einer Datei. Der Animationsbereich zeigt eine kontinuierlich schleifenförmige Animation für lang andauernde Vorgänge oder Vorgänge mit unbestimmter Länge an, z. B. das Erstellen mehrerer Projekte in einer Projektmappe. Und der Designerbereich zeigt die Linien- und Spaltennummer der Cursorposition an.

 Sie können die Statusleiste <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> über die <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Schnittstelle (vom Dienst) abrufen. Darüber hinaus kann sich jedes Objekt, das auf einem Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> ausgeführt wird, durch Implementieren der Schnittstelle als Statusleistenclientobjekt registrieren. Wenn ein Fenster aktiviert wird, fragt Visual Studio das `IVsStatusbarUser` Objekt ab, das in diesem Fenster für die Schnittstelle erstellt wurde. Wenn gefunden, ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> es die Methode auf der zurückgegebenen Schnittstelle auf, und das Objekt kann die Statusleiste innerhalb dieser Methode aktualisieren. Dokumentfenster können z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode verwenden, um Informationen in der Designerregion zu aktualisieren, wenn sie aktiv werden.

 In den folgenden Verfahren wird davon ausgegangen, dass Sie verstehen, wie Sie ein VSIX-Projekt erstellen und einen benutzerdefinierten Menübefehl hinzufügen. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Ändern der Statusleiste
 Dieses Verfahren zeigt Ihnen, wie Sie Text festlegen und abrufen, statischen Text anzeigen und den angezeigten Text im Feedbackbereich der Statusleiste hervorheben.

### <a name="read-and-write-to-the-status-bar"></a>Lesen und Schreiben in die Statusleiste

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **TestStatusBarExtension,** und fügen Sie einen Menübefehl mit dem Namen **TestStatusBarCommand**hinzu.

2. Ersetzen Sie in *TestStatusBarCommand.cs*den`MenuItemCallback`Befehlshandlermethodencode ( ) durch Folgendes:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debuggen.

4. Öffnen Sie das Menü **Extras** in der experimentellen Instanz von Visual Studio. Klicken Sie auf die Schaltfläche **TestStatusBarCommand aufrufen.**

     Sie sollten sehen, dass der Text in der Statusleiste jetzt liest **Wir haben gerade in die Statusleiste geschrieben.** und das angezeigte Meldungsfeld hat denselben Text.

### <a name="update-the-progress-bar"></a>Aktualisieren der Fortschrittsleiste

1. In diesem Verfahren zeigen wir, wie Sie die Fortschrittsleiste initialisieren und aktualisieren.

2. Öffnen *TestStatusBarCommand.cs* Sie die TestStatusBarCommand.cs `MenuItemCallback` Datei, und ersetzen Sie die Methode durch den folgenden Code:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debuggen.

4. Öffnen Sie das Menü **Extras** in der experimentellen Instanz von Visual Studio. Klicken Sie auf **TestStatusBarCommand** aufrufen.

     Sie sollten sehen, dass der Text in der Statusleiste jetzt **Schreiben in die Fortschrittsleiste lautet.** Sie sollten auch sehen, die Fortschrittsleiste wird jede Sekunde für 20 Sekunden aktualisiert. Danach werden die Statusleiste und die Fortschrittsleiste gelöscht.

### <a name="display-an-animation"></a>Anzeigen einer Animation

1. In der Statusleiste wird eine Schleifenanimation angezeigt, die entweder einen lang andauernden Vorgang angibt (z. B. das Erstellen mehrerer Projekte in einer Projektmappe). Wenn diese Animation nicht angezeigt wird, stellen Sie sicher, dass Sie über die richtigen Einstellungen für **die Tools-Optionen** > **Options** verfügen:

     Wechseln Sie zur Registerkarte **Extras** > **Optionen** > **Allgemein,** und deaktivieren Sie die Option **Automatische Anpassung der visuellen Benutzeroberfläche basierend auf der Clientleistung**. Überprüfen Sie dann die Unteroption **Rich Client Visual Experience aktivieren**. Sie sollten nun in der Lage sein, die Animation zu sehen, wenn Sie das Projekt in Ihrer experimentellen Instanz von Visual Studio erstellen.

     In diesem Verfahren zeigen wir die standardmäßige Visual Studio-Animation an, die das Erstellen eines Projekts oder einer Projektmappe darstellt.

2. Öffnen *TestStatusBarCommand.cs* Sie die TestStatusBarCommand.cs `MenuItemCallback` Datei, und ersetzen Sie die Methode durch den folgenden Code:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debuggen.

4. Öffnen Sie das Menü **Extras** in der experimentellen Instanz von Visual Studio, und klicken Sie auf **TestStatusBarCommand aufrufen**.

     Wenn das Meldungsfeld angezeigt wird, sollte die Animation auch in der Statusleiste ganz rechts angezeigt werden. Wenn Sie das Meldungsfeld schließen, wird die Animation ausgeblendet.
