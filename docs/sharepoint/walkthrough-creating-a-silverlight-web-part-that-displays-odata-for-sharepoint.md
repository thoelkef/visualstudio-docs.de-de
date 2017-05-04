---
title: "Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData f&#252;r SharePoint anzeigt | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData f&#252;r SharePoint anzeigt
  SharePoint 2010 ausgiebig die Listendaten mithilfe ODatas verfügbar.  In SharePoint wird der beruhigenden OData\-Dienst vom Dienst ListData.svc implementiert.  Diese exemplarische Vorgehensweise zeigt, wie ein SharePoint\-Webpart erstellt, das eine Silverlight\-Anwendung hostet.  Die Silverlight\-Anwendungsanzeigen SharePoint\-Ankündigungslisteninformationen mit ListData.svc.  Weitere Informationen finden Sie und [SharePoint Foundations\-REST Schnittstelle](http://go.microsoft.com/fwlink/?LinkId=225999) [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   [Erstellen einer Silverlight-Anwendung und -Silverlight-Webparts](#BKMK_creatingSLApp).  
  
-   [Anpassen der Silverlight-Anwendung](#BKMK_customizeSLApp).  
  
-   [Anpassen der Silverlight-Anwendung](#BKMK_customizeSLApp).  
  
-   [Anpassen der Silverlight-Anwendung](#BKMK_customizeSLApp).  
  
-   [Testen des Silverlight-Webparts](#BKMK_testSLApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Erstellen einer Silverlight\-Anwendung und \-Silverlight\-Webparts  
 Zunächst erstellen Sie eine Silverlight\-Anwendung in Visual Studio.  Die Silverlight\-Anwendung ruft Daten aus der SharePoint\-Liste "Ankündigungen" ab, indem sie den ListData.svc\-Dienst verwendet.  
  
> [!NOTE]  
>  Keine Versionen von Silverlight\-, bevor 4,0 die erforderlichen Schnittstellen für Verweise von SharePoint\-Listendaten unterstützen.  
  
#### Um ein Silverlight\-Anwendungs\- und Silverlight\-Webpart erstellen  
  
1.  Klicken Sie auf der Menüleiste **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
2.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Wählen Sie im Vorlagenbereich die Vorlage **SharePoint 2010 Silverlight\-Webpart** aus.  
  
4.  Im Feld **Name** geben Sie SLWebPartTest ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Das Dialogfeld **Assistent zum Anpassen von SharePoint** wird.  
  
5.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie die URL für die SharePoint\-Webserversite, in der Sie die Websitedefinition debuggen möchten, oder verwenden Sie den Standardspeicherort \(http:\/\/*system name*\/\).  
  
6.  Wählen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** das Optionsfeld **Als Farmlösung bereitstellen** aus.  
  
     Obwohl dieses Beispiel eine Farmlösung verwendet, können Silverlight\-Webpartprojekte bereitgestellt werden entweder als Farm oder Sandkastenlösungen.  Weitere Informationen zu Sandkastenlösungen und Farmlösungen, finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Im Abschnitt **Wie soll das Silverlight\-Webpart zugeordnet werden** der Seite **Silverlight\-Konfigurationsinformationen festlegen**, wählen Sie das Optionsfeld **Neues Silverlight\-Projekt erstellen und dem Webpart zuordnen** aus.  
  
8.  Ändern Sie **Name** in SLApplication, legen Sie entweder **Visual Basic** oder **Visual C\#**, **Sprache** fest und legen Sie den **Silverlight 4.0Silverlight\-Version** fest.  
  
9. Wählen Sie die Schaltfläche **Fertig stellen** aus.  Die Projekte werden im **Projektmappen\-Explorer**.  
  
     Die Projektmappe enthält zwei Projekte: eine Silverlight\-Anwendung und ein Silverlight\-Webpart.  Die Silverlight\-Anwendung ruft ab und zeigt die Listendaten von SharePoint angegeben, und das Silverlight\-Webpart hostet die Silverlight\-Anwendung und, können Sie sie in SharePoint anzuzeigen.  
  
##  <a name="BKMK_customizeSLApp"></a> Anpassen der Silverlight\-Anwendung  
 Fügen Sie Code und Entwurfselemente der Silverlight\-Anwendung hinzu.  
  
#### Um die Silverlight\-Anwendung anpassen  
  
1.  Fügen Sie einen Verweis auf System.Windows.Data in die Silverlight\-Anwendung hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für **Verweise**, und wählen Sie dann **Dienstverweis hinzufügen** aus.  
  
    > [!NOTE]  
    >  Wenn Sie Visual Basic verwenden, müssen Sie das Symbol **Alle Dateien anzeigen** oben **Projektmappen\-Explorer** wählen, um den Knoten **Verweise** anzuzeigen.  
  
3.  im Adressfeld des Dialogfelds **Dienstverweis hinzufügen**, geben Sie die URL der SharePoint\-Website, z **http:\/\/MySPSite** ein, und wählen Sie dann die Schaltfläche **Gehe zu** aus.  
  
     Wenn Silverlight den Dienst ListData.svc SharePoint OData lokalisiert, ersetzt sie die Adresse von voller die Dienst\-URL.  In diesem Beispiel ist http:\/\/myserver http:\/\/myserver\/\_vti\_bin\/ListData.svc.  
  
4.  Wählen Sie die Schaltfläche **OK**, um den Dienstverweis auf das Projekt hinzuzufügen, und verwenden Sie den Standarddienstnamen, ServiceReference1.  
  
5.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
6.  Fügen Sie dem Projekt eine neue Datenquelle auf Grundlage des SharePoint\-Dienst hinzu.  Hierzu, in der Menüleiste zu verwenden, wählen Sie **Weitere Fenster**, **Datenquellen**, **Ansicht** aus.  
  
     Das Fenster **Datenquellen** zeigt alle verfügbaren SharePoint\-Listendaten, wie Aufgaben Ankündigungen, und Kalender.  
  
7.  Fügen Sie den Ankündigungslistendaten der Silverlight\-Anwendung hinzu.  Sie können "Ankündigungen" aus dem **Datenquellen** auf den Silverlight\-Designer ziehen.  
  
     Dies erstellt eine Raster\-Steuerelement\-Grenze der Ankündigungsliste der SharePoint\-Website.  
  
8.  Ändern Sie das Rastersteuerelement Größe, damit der Silverlight\-Seite anzupassen.  
  
9. In der MainPage.xaml\-Codedatei MainPage.xaml.cs \(für Visual C\# oder in MainPage.xaml.vb für Visual Basic\), fügen Sie die folgenden Namespaceverweise hinzu.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. Fügen Sie folgenden Variablendeklarationen am Anfang der Klasse hinzu.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. Ersetzen Sie die `UserControl_Loaded` \- Prozedur durch den folgenden Code.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     Stellen Sie sicher, *ServerName* den Platzhalter durch den Namen Ihres Servers zu ersetzen, auf dem SharePoint ausgeführt wird.  
  
12. Fügen Sie die folgende Fehlerbehandlungsprozedur hinzu.  
  
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
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Ändern des Silverlight\-Webparts  
 Ändern Sie eine Eigenschaft im Silverlight\-Webpartprojekt, Silverlight\-Debugging zu aktivieren.  
  
#### Um das Silverlight\-Webpart ändern  
  
1.  Öffnen Sie das Kontextmenü für das Silverlight\-Webpartprojekt \(**SLWebPartTest**\), und wählen Sie dann **Eigenschaften** aus.  
  
2.  Im Fenster **Eigenschaften** wählen Sie die Registerkarte **SharePoint** aus.  
  
3.  Wenn nicht bereits aktiviert ist, aktivieren Sie das Kontrollkästchen **Silverlight\-Debugging aktivieren \(anstelle von Skript\-Debugging\)**.  
  
4.  Speichern Sie das Projekt.  
  
##  <a name="BKMK_testSLApp"></a> Testen des Silverlight\-Webparts  
 Testen Sie das neue Silverlight\-Webpart in SharePoint, um sicherzustellen, dass es die SharePoint\-Listendaten korrekt anzeigt.  
  
#### Um das Silverlight\-Webpart testen  
  
1.  Drücken Sie die F5\-TASTE, um die SharePoint\-Lösung erstellen und auszuführen.  
  
2.  In SharePoint im Menü **Websiteaktionen**, wählen Sie **Neues Zeichenblatt** aus.  
  
3.  Im Dialogfeld **Neues Zeichenblatt** Geben Sie einen Titel, wie SL\-Webpart\-Test ein, und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
4.  Im Seitendesigner auf der Registerkarte **Bearbeitungstools**, wählen Sie **Einfügen** aus.  
  
5.  Auf der Registerleiste wählen Sie **Webpart** aus.  
  
6.  Im Feld **Kategorien** wählen Sie den Ordner **Benutzerdefiniert** aus.  
  
7.  In der Liste **Webparts** wählen Sie das Silverlight\-Webpart aus, und wählen Sie die Schaltfläche **Hinzufügen**, um das Webpart zum Designer hinzufügen.  
  
8.  Nachdem Sie alle Erweiterungen der Webseite festgelegt haben, die Sie verwenden möchten, wählen Sie die Registerkarte **Seite**, und wählen Sie dann die Schaltfläche **Speichern und schließen &**  auf der Symbolleiste aus.  
  
     Das Silverlight\-Webpart sollte Werbungsdaten von der SharePoint\-Website jetzt anzeigen.  Standardmäßig wird die Seite in der Websiteseitenliste in SharePoint gespeichert.  
  
    > [!NOTE]  
    >  Wenn es auf Daten in Silverlight domänenübergreifend zugreift, schützt Silverlight und Sicherheitslücken, die verwendet werden können, um Webanwendungen ausgelegt.  Wenn Probleme auf, wenn auf Remotedaten in Silverlight zugegriffen werden, finden [Ein Dienst bereitstellen zu Domänen\-Grenzen](http://go.microsoft.com/fwlink/?LinkId=223276) auftreten.  
  
## Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  