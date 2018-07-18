---
title: Erweitern die Statusleiste | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a766e0c607d4d669fada794e1cf0779559f2346b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130491"
---
# <a name="extending-the-status-bar"></a>Erweitern Sie auf der Statusleiste
Sie können die Statusleiste von Visual Studio am unteren Rand der IDE verwenden, um Informationen anzuzeigen.  
  
 Wenn Sie auf die Statusleiste erweitern, zeigen Sie Informationen und UI in vier Bereiche: die Feedbackbereich, Statusleiste, des animationsbereichs und des Designerbereichs. Die Feedbackbereich können Sie Text anzeigen, und markieren Sie den angezeigten Text. Die Statusanzeige zeigt Angaben zum Fortschritt für kurzer Vorgänge, z. B. eine Datei zu speichern. Die Animationsbereich zeigt eine fortlaufend in Schleife Animation für lang andauernde oder Operationen unbestimmt Länge, wie z. B. das Erstellen von mehreren Projekten in einer Projektmappe an. Und der Bereich des Designers zeigt die Anzahl Zeilen- und Spaltennummer der Cursorposition.  
  
 Erhalten Sie mithilfe die Statusleiste der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Schnittstelle (aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Service). Darüber hinaus jedes Objekt, positioniert auf einen Fensterrahmen als Registrieren einer Statusleisten-Clientobjekt, das durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Schnittstelle. Wenn ein Fenster aktiviert ist, fragt Visual Studio das Objekt, positioniert auf das Fenster für die `IVsStatusbarUser` Schnittstelle. Wenn gefunden, er ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode für die zurückgegebene Schnittstelle und das Objekt kann in der Statusleiste aus innerhalb dieser Methode aktualisieren. Windows, z. B. zu dokumentieren, können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode, um die Informationen in den Bereich des Designers zu aktualisieren, wenn sie aktiv sind.  
  
 Die folgenden Verfahren wird davon ausgegangen, dass Sie wissen, wie ein VSIX-Projekt erstellen, und fügen Sie einen benutzerdefinierten Befehl hinzu. Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Ändern der Statusleiste  
 Dieses Verfahren wird gezeigt, wie zum Festlegen und Abrufen von Text, statischen Text angezeigt und markieren Sie den angezeigten Text in die Feedbackbereich der Statusleiste.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Lesen und Schreiben in der Statusleiste  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **TestStatusBarExtension** und Hinzufügen eines Menübefehls mit dem Namen **TestStatusBarCommand**.  
  
2.  Ersetzen Sie im TestStatusBarCommand.cs den Befehl Code Ereignishandlermethode (MenuItemCallback) wie folgt aus:  
  
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
  
3.  Kompilieren Sie des Codes, und starten Sie das Debuggen.  
  
4.  Öffnen der **Tools** Menü in der experimentellen Instanz von Visual Studio. Klicken Sie auf die **TestStatusBarCommand Aufrufen** Schaltfläche.  
  
     Sie sehen, das den Text in der Statusleiste jetzt Lesevorgänge **"Wir soeben geschrieben haben auf der Statusleiste angezeigt."** ein, und klicken Sie im Meldungsfeld hat den gleichen Text.  
  
#### <a name="updating-the-progress-bar"></a>Die Statusanzeige wird aktualisiert.  
  
1.  In diesem Verfahren veranschaulichen wir, initialisieren und die Statusanzeige zu aktualisieren.  
  
2.  Öffnen Sie die Datei TestStatusBarCommand.cs, und Ersetzen Sie die MenuItemCallback-Methode, durch den folgenden Code:  
  
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
  
3.  Kompilieren Sie des Codes, und starten Sie das Debuggen.  
  
4.  Öffnen der **Tools** Menü in der experimentellen Instanz von Visual Studio. Klicken Sie auf **TestStatusBarCommand Aufrufen** Schaltfläche.  
  
     Sollte angezeigt werden, die Text in der Statusleiste jetzt Lesevorgänge **"Schreiben in der Statusanzeige auf."** Die Statusanzeige, die pro Sekunde für 20 Sekunden aktualisiert werden sollte auch angezeigt werden. Danach werden die Statusleiste und die Statusanzeige gelöscht.  
  
#### <a name="displaying-an-animation"></a>Eine Animation anzeigen  
  
1.  Die Statusleiste zeigt einer Schleifen Animation an, die entweder ein Hinweis darauf ein langer Vorgang (z. B. das Erstellen von mehreren Projekten in einer Projektmappe) an. Wenn Sie diese Animation nicht angezeigt werden, stellen Sie sicher, dass die richtige **Extras / Optionen** Einstellungen:  
  
     Wechseln Sie zu der **Extras/Optionen / Allgemein** Registerkarte, und deaktivieren Sie **automatisch visuelle Darstellung, die basierend auf der Clientleistung anpassen**. Überprüfen Sie die untergeordnete Option **visuelle Clientdarstellung aktivieren**. Sie sollten jetzt möglich, um die Animation anzuzeigen, wenn Sie das Projekt in der experimentellen Instanz von Visual Studio erstellen.  
  
     In diesem Verfahren wird die standardmäßige Visual Studio-Animation Erstellen eines Projekts oder einer Projektmappe dar angezeigt.  
  
2.  Öffnen Sie die Datei TestStatusBarCommand.cs, und Ersetzen Sie die MenuItemCallback-Methode, durch den folgenden Code:  
  
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
  
3.  Kompilieren Sie des Codes, und starten Sie das Debuggen.  
  
4.  Öffnen der **Tools** in der experimentellen Instanz von Visual Studio, und klicken Sie im Menü **aufrufen TestStatusBarCommand**.  
  
     Wenn Sie im Meldungsfeld angezeigt wird, sollte auch in der Statusleiste Animation ganz rechts angezeigt werden. Wenn Sie das Meldungsfeld schließen, verschwindet die Animation.