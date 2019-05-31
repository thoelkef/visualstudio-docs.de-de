---
title: Erstellen Sie Silverlight-Webpart anzeigen von OData für SharePoint
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f248ce4403e771d9ab8b6d13fe55fd5ca1c960d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401134"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt
  SharePoint 2010 stellt die Daten mithilfe von OData. In SharePoint wird der OData-Dienst von den RESTful-Dienst ListData.svc implementiert. In dieser exemplarischen Vorgehensweise zeigt, wie Sie einen SharePoint-Webpart erstellen, eine Silverlight-Anwendung gehostet, wird. Die Silverlight-Anwendung zeigt Listen Sie Informationen zu SharePoint-Ankündigung ListData.svc. Weitere Informationen finden Sie unter [SharePoint Foundation-REST-Schnittstelle](http://go.microsoft.com/fwlink/?LinkId=225999) und [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Erstellen eines Silverlight-Anwendung und die Silverlight-Webparts
 Erstellen Sie zunächst eine Silverlight-Anwendung in Visual Studio. Die Silverlight-Anwendung ruft Daten aus der Liste der SharePoint-Ankündigungen mithilfe des Diensts ListData.svc ab.

> [!NOTE]
> Keine Versionen von Silverlight vor 4.0 unterstützt die erforderlichen Schnittstellen zum Verweisen auf die SharePoint-Listendaten.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Zum Erstellen eines Silverlight-Anwendung und die Silverlight-Webparts

1. Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.

2. Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.

3. Wählen Sie im Vorlagenbereich die **SharePoint 2010 Silverlight-Webpart** Vorlage.

4. In der **Namen** geben **SLWebPartTest** und wählen Sie dann die **OK** Schaltfläche.

    Die **SharePoint Customization Wizard** Dialogfeld wird angezeigt.

5. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL der SharePoint-Server-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden Sie den Standardspeicherort (http://<em>Systemname</em>/) .

6. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus.

    Obwohl in diesem Beispiel eine farmlösung verwendet wird, können die Silverlight-Webpart Webprojekte entweder als Farm oder als Sandbox-Lösungen bereitgestellt werden. Weitere Informationen zu sandkastenlösungen und-farmlösungen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).

7. In der **wie möchten Sie das Silverlight-Webpart zuordnen** Teil der **Silverlight-Konfigurationsinformationen geben** Seite die **Erstellen eines neuen Silverlight-Projekts und Ordnen sie das Webpart** Optionsfeld aus.

8. Ändern der **Namen** zu **SLApplication**legen **Sprache** entweder **Visual Basic** oder **Visual C#-** , und legen Sie dann **Silverlight-Version** zu **Silverlight 4.0**.

9. Wählen Sie die **Fertig stellen** Schaltfläche. Die Projekte angezeigt, **Projektmappen-Explorer**.

     Die Projektmappe enthält zwei Projekte: ein Silverlight-Anwendung und eines Silverlight-WebParts. Die Silverlight-Anwendung ruft ab und zeigt die Listendaten aus SharePoint, und das Silverlight-Webpart hostet, die Silverlight-Anwendung, sodass Sie für die Anzeige in SharePoint.

## <a name="customize-the-silverlight-application"></a>Anpassen der Silverlight-Anwendung
 Fügen Sie Code und Entwurf Elemente in der Silverlight-Anwendung hinzu.

#### <a name="to-customize-the-silverlight-application"></a>Anpassen die Silverlight-Anwendung

1. Fügen Sie einen Assemblyverweis auf System.Windows.Data hinzu, in der Silverlight-Anwendung. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen oder Entfernen von verweisen mithilfe des Dialogfelds "Verweis" hinzufügen "](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Verweise**, und wählen Sie dann **Hinzufügen eines Dienstverweises**.

    > [!NOTE]
    > Wenn Sie Visual Basic verwenden, müssen Sie auswählen der **alle Dateien anzeigen** Symbol am oberen Rand **Projektmappen-Explorer** zum Anzeigen der **Verweise** Knoten.

3. Im Feld Adresse ein, der die **Dienstverweis hinzufügen** Dialogfeld Geben Sie die URL der SharePoint-Website, z. B. **http://MySPSite** , und wählen Sie dann die **wechseln** Schaltfläche.

     Wenn Silverlight den SharePoint-OData-Dienst ListData.svc findet, wird die Adresse mit den vollständigen Dienst-URL ersetzt. In diesem Beispiel http://myserver wird http://myserver/_vti_bin/ListData.svc.

4. Wählen Sie die **OK** Schaltfläche, um den Dienstverweis dem Projekt hinzuzufügen, und verwenden Sie den standarddienstnamen ServiceReference1.

5. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

6. Fügen Sie dem Projekt basierend auf dem SharePoint-Dienst eine neue Datenquelle hinzu. Wählen Sie hierzu auf der Menüleiste **Ansicht** > **Other Windows** > **Datenquellen**.

     Die **Datenquellen** Fenster zeigt alle verfügbaren SharePoint-Listendaten, z. B. Aufgaben, Ankündigungen und Kalender.

7. Fügen Sie die Listendaten von Ankündigungen für die Silverlight-Anwendung hinzu. Sie können "Ankündigungen" von Ziehen der **Datenquellen** auf Silverlight-Designer.

     Dadurch wird ein Rastersteuerelement gebunden, in der SharePoint-Website-Ankündigungen-Liste erstellt.

8. Größe des Grid-Steuerelements entsprechend die Silverlight-Seite.

9. In der Codedatei "MainPage.xaml" ( *"MainPage.Xaml.cs"* für Visual c# oder *"MainPage.Xaml.vb"* für Visual Basic), fügen Sie die folgenden Namespaceverweise hinzu.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using statements.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Fügen Sie am oberen Rand der Klasse die folgenden Variablendeklarationen hinzu.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. Ersetzen Sie die `UserControl_Loaded` Prozedur durch Folgendes.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     Ersetzen Sie die *ServerName* Platzhalter mit dem Namen des Servers, auf dem SharePoint ausgeführt wird.

12. Fügen Sie das folgende Verfahren für die Fehlerbehandlung hinzu.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Ändern Sie das Silverlight-Webpart
 Ändern einer Eigenschaft in der Silverlight-Webpartprojekts Silverlight-debugging aktivieren.

#### <a name="to-modify-the-silverlight-web-part"></a>So ändern Sie das Silverlight-Webpart

1. Öffnen Sie das Kontextmenü für das Silverlight-Webpartprojekts (**SLWebPartTest**), und wählen Sie dann **Eigenschaften**.

2. In der **Eigenschaften** Fenster, wählen Sie die **SharePoint** Registerkarte.

3. Wenn sie nicht bereits ausgewählt ist, wählen Sie die **aktivieren Silverlight-debugging (anstelle von Skriptdebuggen)** Kontrollkästchen.

4. Speichern Sie das Projekt.

## <a name="test-the-silverlight-web-part"></a>Testen Sie das Silverlight-Webpart
 Testen Sie das neue Silverlight-Webpart in SharePoint. Damit stellen Sie sicher, dass sie die SharePoint-Listendaten korrekt angezeigt.

#### <a name="to-test-the-silverlight-web-part"></a>So testen Sie das Silverlight-Webpart

1. Wählen Sie die **F5** Schlüssel erstellen und Ausführen der SharePoint-Lösung.

2. In SharePoint auf die **Websiteaktionen** Menü wählen **neue Seite**.

3. In der **neue Seite** Dialogfeld Geben Sie einen Titel ein, z. B. **SL Teil Webtest**, und wählen Sie dann die **erstellen** Schaltfläche.

4. In der Designer auf die **Bearbeitungstools** Registerkarte **einfügen**.

5. Wählen Sie auf der Registerkartenleiste **Webpart**.

6. In der **Kategorien** wählen die **benutzerdefinierte** Ordner.

7. In der **Webparts** aus, wählen Sie das Silverlight-Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche, um das Webpart zum Designer hinzufügen.

8. Nachdem Sie alle der Erweiterungen zu der Webseite, die Sie möchten vorgenommen haben, wählen Sie die **Seite** Registerkarte, und wählen Sie dann die **speichern und schließen** auf der Symbolleiste auf die Schaltfläche.

     Das Silverlight-Webpart sollte jetzt Ankündigung-Daten aus der SharePoint-Website angezeigt werden. Standardmäßig wird die Seite in der Liste der Seiten der Website in SharePoint gespeichert.

    > [!NOTE]
    > Beim Zugriff auf Daten in Silverlight domänenübergreifend schützt Silverlight, vor Sicherheitsrisiken, die verwendet werden können, um Webanwendungen auszunutzen. Wenn Sie Probleme beim Zugriff auf remote-Daten in Silverlight haben, finden Sie unter [vornehmen einer Service Available Across Domain Boundaries](http://go.microsoft.com/fwlink/?LinkId=223276).

## <a name="see-also"></a>Siehe auch
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
