---
title: "Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, die OData für SharePoint anzeigt | Microsoft Docs"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 3c2c66490e0eb46508fce0f346fe44563548b407
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt
  SharePoint 2010 macht seine Daten mithilfe von OData. In SharePoint wird die OData-Dienst von RESTful-Dienst ListData.svc implementiert. In dieser exemplarischen Vorgehensweise wird gezeigt, wie einen SharePoint-Webpart erstellt, der eine Silverlight-Anwendung hostet. Die Silverlight-Anwendung zeigt Listen Sie Informationen zu SharePoint-Ankündigung mithilfe von ListData.svc. Weitere Informationen finden Sie unter [SharePoint Foundation-REST-Schnittstelle](http://go.microsoft.com/fwlink/?LinkId=225999) und [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Erstellen einer Silverlight-Anwendung und die Silverlight-Webpart  
 Erstellen Sie zuerst eine Silverlight-Anwendung in Visual Studio. Die Silverlight-Anwendung ruft Daten aus der Liste der SharePoint-Ankündigungen mithilfe des ListData.svc-Diensts ab.  
  
> [!NOTE]  
>  Keine Versionen von Silverlight 4.0 unterstützt die erforderlichen Schnittstellen zum Verweisen auf die SharePoint-Listendaten.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Zum Erstellen einer Silverlight-Anwendung und die Silverlight-Webpart  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  Klicken Sie im Bereich "Vorlagen" Wählen Sie die **SharePoint 2010 Silverlight-Webpart** Vorlage.  
  
4.  In der **Namen** geben **SLWebPartTest** und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** Dialogfeld wird angezeigt.  
  
5.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite Geben Sie die URL für die SharePoint-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden den Standardspeicherort (http://*Systemname*/) .  
  
6.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld.  
  
     Obwohl in diesem Beispiel wird eine farmlösung verwendet wird, können die Silverlight-Webpart Webprojekte als Farm oder sandkastenlösungen bereitgestellt werden. Weitere Informationen über sandkastenlösungen und-farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  In der **wie möchten Sie das Silverlight-Webpart zuordnen** Teil der **Silverlight-Konfigurationsinformationen geben** Seite der **Erstellen eines neuen Silverlight-Projekts und Ordnen Sie es mit dem Webpart** Optionsfeld.  
  
8.  Ändern der **Namen** auf **SLApplication**legen **Sprache** entweder **Visual Basic** oder **Visual C#-**, und legen Sie dann **Silverlight-Version** auf **Silverlight 4.0**.  
  
9. Wählen Sie die **Fertig stellen** Schaltfläche. Die Projekte werden in **Projektmappen-Explorer**.  
  
     Die Projektmappe enthält zwei Projekte: eine Silverlight-Anwendung und einem Silverlight-Webpart. Die Silverlight-Anwendung ruft ab und zeigt die Listendaten aus SharePoint und des Silverlight-Webparts gehostet, die Silverlight-Anwendung, und aktivieren Sie für die Anzeige in SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Anpassen der Silverlight-Anwendung  
 Fügen Sie Code und Entwurf Elemente für die Silverlight-Anwendung hinzu.  
  
#### <a name="to-customize-the-silverlight-application"></a>Zum Anpassen der Silverlight-Anwendung  
  
1.  Fügen Sie einen Assemblyverweis auf System.Windows.Data hinzu, in der Silverlight-Anwendung. Weitere Informationen finden Sie unter [wie: Hinzufügen oder Entfernen von verweisen mithilfe des Dialogfelds der hinzufügen-Verweis](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Verweise**, und wählen Sie dann **Hinzufügen eines Dienstverweises**.  
  
    > [!NOTE]  
    >  Wenn Sie Visual Basic verwenden, müssen Sie auswählen der **alle Dateien anzeigen** Symbol am oberen Rand **Projektmappen-Explorer** zum Anzeigen der **Verweise** Knoten.  
  
3.  In das Adressfeld von der **Hinzufügen eines Dienstverweises** Dialogfeld Geben Sie die URL der SharePoint-Website, z. B. **http://MySPSite**, und wählen Sie dann die **wechseln** Schaltfläche.  
  
     Wenn Silverlight des SharePoint-OData-Diensts ListData.svc findet, wird die Adresse mit den vollständigen Dienst-URL ersetzt. In diesem Beispiel wird http://myserver http://myserver/_vti_bin/ListData.svc.  
  
4.  Wählen Sie die **OK** Schaltfläche zum Hinzufügen des Dienstverweises zum Projekt, und verwenden Sie den standarddienstnamen ServiceReference1.  
  
5.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
6.  Fügen Sie dem Projekt basierend auf dem SharePoint-Dienst eine neue Datenquelle hinzu. Klicken Sie hierzu in der Menüleiste wählen **Ansicht**, **Weitere Fenster**, **Datenquellen**.  
  
     Die **Datenquellen** Fenster zeigt alle verfügbaren SharePoint-Listendaten, wie z. B. Kalender, Aufgaben und Ankündigungen.  
  
7.  Fügen Sie die Ankündigungen Listendaten, für die Silverlight-Anwendung. Sie können "Ankündigungen" ziehen, aus der **Datenquellen** Fenster in den Silverlight-Designer.  
  
     Dies erstellt ein Grid-Steuerelement, das auf der SharePoint-Website Ankündigungsliste gebunden.  
  
8.  Ändern Sie das Rastersteuerelement entsprechend die Silverlight-Seite.  
  
9. Klicken Sie in der Datei "MainPage.xaml" ("MainPage.Xaml.cs" für Visual c#) oder "MainPage.Xaml.vb" für Visual Basic-Codedatei die folgenden Namespaceverweise hinzuzufügen.  
  
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
   
11. Ersetzen Sie die `UserControl_Loaded` mit den folgenden Verfahren.  
  
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
     Achten Sie darauf, dass Sie ersetzen die *ServerName* Platzhalter mit dem Namen des Servers, auf dem SharePoint ausgeführt wird.  
  
12. Fügen Sie die folgenden Fehlerbehandlungsverfahren hinzu.  
  
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
       
## <a name="modifying-the-silverlight-web-part"></a>Ändern das Silverlight-Webpart  
 Ändern einer Eigenschaft in der Silverlight-Webpartprojekt Silverlight-debugging aktivieren.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>So ändern Sie das Silverlight-Webpart  
  
1.  Öffnen Sie das Kontextmenü für die Silverlight-Webpartprojekts (**SLWebPartTest**), und wählen Sie dann **Eigenschaften**.  
  
2.  In der **Eigenschaften** Fenster, wählen Sie die **SharePoint** Registerkarte.  
  
3.  Wenn es nicht bereits ausgewählt ist, wählen Sie die **aktivieren Silverlight-debugging (anstelle von Skript-debugging)** Kontrollkästchen.  
  
4.  Speichern Sie das Projekt.  
  
##  <a name="testing-the-silverlight-web-part"></a>Testen des Silverlight-Webparts  
 Testen Sie das neue Silverlight-Webpart in SharePoint. Damit stellen Sie sicher, dass die SharePoint-Listendaten ordnungsgemäß angezeigt.  
  
#### <a name="to-test-the-silverlight-web-part"></a>So testen Sie das Silverlight-Webpart  
  
1.  Wählen Sie die F5-Taste zum Erstellen und Ausführen der SharePoint-Lösung.  
  
2.  In SharePoint auf die **Websiteaktionen** Menü wählen **neue Seite**.  
  
3.  In der **neue Seite** Dialogfeld, geben Sie einen Titel ein, z. B. **"SL" Teil Webtest**, und wählen Sie dann die **erstellen** Schaltfläche.  
  
4.  In der Seiten-Designer auf die **Bearbeitungstools** Registerkarte **einfügen**.  
  
5.  Wählen Sie in der Registerkartenleiste **Webpart**.  
  
6.  In der **Kategorien** wählen Sie die **benutzerdefinierte** Ordner.  
  
7.  In der **Webparts** aus, wählen Sie das Silverlight-Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche, um das Webpart zum Designer hinzufügen.  
  
8.  Nachdem Sie alle Virtual Machine Additions auf der Webseite, die Sie möchten vorgenommen haben, wählen Sie die **Seite** Registerkarte, und wählen Sie dann die **speichern und schließen** auf der Symbolleiste auf die Schaltfläche.  
  
     Das Silverlight-Webpart sollte jetzt Ankündigung Daten aus der SharePoint-Website angezeigt werden. Standardmäßig wird die Seite in der Liste der Seiten der Website in SharePoint gespeichert.  
  
    > [!NOTE]  
    >  Zugreifen auf Daten in Silverlight domänenübergreifend schützt Silverlight vor Sicherheitsrisiken, die verwendet werden können, um Webanwendungen auszunutzen. Wenn Sie Probleme beim Zugriff auf remote-Daten in Silverlight auftreten, finden Sie unter [machen einen Service Available Across Domain Boundaries](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Bereitstellen, Veröffentlichen und Upgraden von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
