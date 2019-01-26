---
title: Erweitern der Statusleiste | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20502be32cb3206431316a062ab1ee898c66e274
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956414"
---
# <a name="extend-the-status-bar"></a>Erweitern der Statusleiste
Sie können die Statusleiste von Visual Studio am unteren Rand der IDE verwenden, um Informationen anzuzeigen.  
  
 Wenn Sie auf die Statusleiste erweitern, zeigen Sie Informationen und Benutzeroberfläche in vier Regionen: die Feedbackbereich, Statusleiste, des animationsbereichs und den Bereich des Designers. Die Feedbackbereich können Sie Text anzeigen, und markieren Sie den angezeigten Text. Die Statusanzeige zeigt schrittweisen Fortschritt für kurze Vorgänge wie das Speichern einer Datei. Der Animationsbereich zeigt eine Animation kontinuierlich in Schleife, lang andauernde oder Operationen unbestimmten Länge, wie z. B. das Erstellen von mehreren Projekten in einer Projektmappe an. Und der Bereich des Designers die Zeile und Spalte Anzahl von der Cursorposition.  
  
 Erhalten Sie mit die Statusleiste der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Schnittstelle (aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Service). Darüber hinaus ein Objekt, positioniert auf der einen Fensterrahmen als Registrieren einer Statusleisten-Clientobjekt, das durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Schnittstelle. Wenn ein Fenster aktiviert ist, fragt Visual Studio das Objekt, positioniert auf das Fenster für die `IVsStatusbarUser` Schnittstelle. Wenn gefunden, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode für die zurückgegebene Schnittstelle und das Objekt kann die Statusleiste von innerhalb der betreffenden Methode aktualisieren. Dokumentfenster, z. B., können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode, um die Informationen in den Bereich des Designers zu aktualisieren, wenn sie aktiv sind.  
  
 Die folgenden Verfahren wird davon ausgegangen, dass Sie verstehen, wie ein VSIX-Projekt erstellen, und fügen Sie einen benutzerdefinierten Befehl hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modify-the-status-bar"></a>Ändern der Statusleiste  
 Dieses Verfahren zeigt, wie Sie festlegen und Abrufen von Text, statischen Text anzuzeigen und markieren Sie den angezeigten Text in die Feedbackbereich der Statusleiste.  
  
### <a name="read-and-write-to-the-status-bar"></a>Lesen und Schreiben in der Statusleiste  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **TestStatusBarExtension** und Hinzufügen eines Menübefehls mit dem Namen **TestStatusBarCommand**.  
  
2.  In *TestStatusBarCommand.cs*, ersetzen Sie die Methode befehlshandlercode (`MenuItemCallback`) durch Folgendes:  
  
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
  
3.  Kompilieren Sie des Codes und mit dem Debuggen beginnen.  
  
4.  Öffnen der **Tools** Menü in der experimentellen Instanz von Visual Studio. Klicken Sie auf die **aufrufen TestStatusBarCommand** Schaltfläche.  
  
     Sollte angezeigt werden, den Text in der Statusleiste jetzt Lesevorgänge **wir gerade geschrieben haben, klicken Sie auf der Statusleiste angezeigt.** und klicken Sie im daraufhin angezeigten Nachrichtenfeld hat den gleichen Text.  
  
### <a name="update-the-progress-bar"></a>Die Statusanzeige zu aktualisieren  
  
1.  In diesem Verfahren wird erfahren, wie zu initialisieren und die Statusanzeige zu aktualisieren.  
  
2.  Öffnen der *TestStatusBarCommand.cs* -Datei und Ersetzen Sie die `MenuItemCallback` Methode durch den folgenden Code:  
  
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
  
3.  Kompilieren Sie des Codes und mit dem Debuggen beginnen.  
  
4.  Öffnen der **Tools** Menü in der experimentellen Instanz von Visual Studio. Klicken Sie auf **aufrufen TestStatusBarCommand** Schaltfläche.  
  
     Sollte angezeigt werden, den Text in der Statusleiste jetzt Lesevorgänge **Schreiben in die Statusanzeige.** Die Statusanzeige, die pro Sekunde für 20 Sekunden aktualisiert werden sollte auch angezeigt werden. Danach werden die Statusleiste und die Statusanzeige gelöscht.  
  
### <a name="display-an-animation"></a>Eine Animation anzeigen  
  
1.  Die Statusleiste zeigt einer Schleifen Animation, die entweder angibt ein lang andauernder Vorgang (z. B. das Erstellen von mehreren Projekten in einer Projektmappe) an. Wenn Sie diese Animation nicht angezeigt werden, stellen Sie sicher, dass die richtige **Tools** > **Optionen** Einstellungen:  
  
     Wechseln Sie zu der **Tools** > **Optionen** > **allgemeine** Registerkarte, und deaktivieren Sie **automatisch die visuelle Darstellung, die basierend auf der Clientleistung anpassen Leistung**. Klicken Sie dann das Kontrollkästchen untergeordnete **Umfassende visuelle Clientdarstellung aktivieren**. Sie sollten jetzt in der Lage zum Anzeigen der Animation, wenn Sie das Projekt in der experimentellen Instanz von Visual Studio erstellen.  
  
     In diesem Verfahren wird die standardmäßige Visual Studio-Animation die darstellt, erstellen ein Projekt oder eine Projektmappe angezeigt.  
  
2.  Öffnen der *TestStatusBarCommand.cs* -Datei und Ersetzen Sie die `MenuItemCallback` Methode durch den folgenden Code:  
  
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
  
3.  Kompilieren Sie des Codes und mit dem Debuggen beginnen.  
  
4.  Öffnen der **Tools** in der experimentellen Instanz von Visual Studio, und klicken Sie im Menü **aufrufen TestStatusBarCommand**.  
  
     Wenn das Meldungsfeld angezeigt wird, sollte auch die Animation in der Statusleiste ganz rechts angezeigt werden. Wenn Sie das Meldungsfeld zu schließen, verschwindet die Animation.