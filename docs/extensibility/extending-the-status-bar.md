---
title: "Erweitern Sie die Statusleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Statusleisten Informationen über Statusleisten"
  - "Statusleisten, Übersicht"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Erweitern Sie die Statusleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Visual Studio\-Statusleiste können am unteren Rand der IDE Sie die Informationen anzuzeigen.  
  
 Wenn Sie die Statusleiste erweitern, zeigen Sie Informationen und Benutzeroberfläche in vier Bereiche: Bereich für Feedback, die Statusanzeige zu bewegen, die Animation Region und den Bereich des Designers. Die Feedback\-Region können Sie Text anzeigen, und markieren Sie den angezeigten Text. Die Statusanzeige zeigt schrittweisen Fortschritt für kurzer Vorgänge wie das Speichern einer Datei. Die Animation Region zeigt eine Animation kontinuierlich durchlaufen, lang andauernde oder Operationen nicht festgelegte Länge, wie z. B. das Erstellen von mehreren Projekten in einer Projektmappe an. Und der Bereich des Designers zeigt die Zeilen\- und die Anzahl der Cursorposition.  
  
 Erhalten Sie mithilfe die Statusleiste der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Schnittstelle \(aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Service\). Darüber hinaus alle Objekte, die auf einen Fensterrahmen positioniert als registrieren eine Statusleiste Clientobjekt durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Schnittstelle. Wenn ein Fenster aktiviert wird, fragt Visual Studio das Objekt platziert, die in diesem Fenster für die `IVsStatusbarUser` Schnittstelle. Wenn gefunden, es Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> \-Methode auf die zurückgegebene Schnittstelle und das Objekt kann in dieser Methode die Statusleiste aus aktualisieren. Windows, z. B. zu dokumentieren, können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode, um die Informationen in den Bereich des Designers zu aktualisieren, wenn sie aktiv sind.  
  
 Die folgenden Verfahren wird davon ausgegangen, dass Sie wissen, wie erstellen Sie ein VSIX\-Projekt, und fügen Sie einen benutzerdefinierten Befehl hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Ändern der Statusleiste  
 Dieses Verfahren zeigt, wie festgelegt und Text abrufen, statischen Text anzuzeigen, und markieren Sie den angezeigten Text in der Statusleiste der Feedback\-Region.  
  
#### Lesen und Schreiben in der Statusleiste  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **TestStatusBarExtension** und fügen Sie einen Befehl mit dem Namen **TestStatusBarCommand**.  
  
2.  Ersetzen Sie den Befehl Methodencode \(MenuItemCallback\) in TestStatusBarCommand.cs durch den folgenden:  
  
    ```c#  
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
  
4.  Öffnen Sie die **Tools** in der experimentellen Instanz von Visual Studio im Menü. Klicken Sie auf die **aufrufen TestStatusBarCommand** Schaltfläche.  
  
     Sollte der Text in der Statusleiste jetzt Lesevorgänge **"Wir soeben geschrieben haben auf der Statusleiste angezeigt."** und das Meldungsfeld enthält des gleichen Text.  
  
#### Die Statusanzeige wird aktualisiert.  
  
1.  In diesem Verfahren wird gezeigt, wie initialisiert und die Statusanzeige zu aktualisieren.  
  
2.  Öffnen Sie die Datei TestStatusBarCommand.cs, und Ersetzen Sie die MenuItemCallback\-Methode durch den folgenden Code:  
  
    ```c#  
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
  
4.  Öffnen Sie die **Tools** in der experimentellen Instanz von Visual Studio im Menü. Klicken Sie auf **TestStatusBarCommand Aufrufen** Schaltfläche.  
  
     Sollte angezeigt werden, die den Text in der Statusleiste jetzt Lesevorgänge **"Schreiben in die Leiste Fortschritt"** Außerdem sollte die Statusanzeige, die pro Sekunde für 20 Sekunden aktualisiert. Danach werden die Statusleiste und die Statusanzeige gelöscht.  
  
#### Eine Animation anzeigen  
  
1.  Die Statusleiste zeigt einer Schleifen Animation, die entweder ein Hinweis darauf einen langer Vorgang \(z. B. das Erstellen von mehreren Projekten in einer Projektmappe\). Wenn diese Animation nicht angezeigt wird, stellen Sie sicher, dass der richtige **Extras \/ Optionen** Einstellungen:  
  
     Klicken Sie auf die **Extras\/Optionen \/ Allgemein** Registerkarte, und deaktivieren Sie **automatisch die visuelle Darstellung, die basierend auf der Clientleistung anpassen**. Klicken Sie dann das Kontrollkästchen Unterordner **Umfassende visuelle Clientdarstellung aktivieren**. Sie sollten jetzt in der Lage, die Animation zu sehen, wenn Sie das Projekt in der experimentellen Instanz von Visual Studio erstellen.  
  
     In diesem Verfahren zeigen wir die standardmäßige Visual Studio\-Animation, die Erstellen eines Projekts oder einer Projektmappe darstellt.  
  
2.  Öffnen Sie die Datei TestStatusBarCommand.cs, und Ersetzen Sie die MenuItemCallback\-Methode durch den folgenden Code:  
  
    ```c#  
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
  
4.  Öffnen Sie die **Tools** in der experimentellen Instanz von Visual Studio, und klicken Sie im Menü **aufrufen TestStatusBarCommand**.  
  
     Wenn das Meldungsfeld angezeigt wird, sollte auch die Animation in der Statusleiste ganz rechts angezeigt werden. Wenn Sie das Meldungsfeld schließen, verschwindet die Animation.