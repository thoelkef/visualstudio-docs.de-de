---
title: 'Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5db5e9408a64df80311667267561ee69234fd7d5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852744"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Profilerstellungstools in Visual Studio gezeigt, um die Leistung einer SharePoint-Anwendung zu optimieren. Bei der Beispielanwendung handelt es sich um einen SharePoint-Funktionsereignisempfänger, der eine Leerlaufschleife enthält, welche die Leistung des Funktionsereignisempfängers reduziert. Visual Studio-Profiler ermöglicht Ihnen, Auffinden und beseitigen die teuersten (langsamsten) Teil des Projekts, auch bekannt als die *Langsamster Pfad*.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
- [Hinzufügen einer Funktion und den Funktionsereignisempfänger](#BKMK_AddFtrandFtrEvntReceiver).  
  
- [Konfigurieren und Bereitstellen der SharePoint-Anwendung](#BKMK_ConfigSharePointApp).  
  
- [Ausführen der SharePoint-Anwendung](#BKMK_RunSPApp).  
  
- [Anzeigen und Interpretieren der Profilerstellungsergebnisse](#BKMK_ViewResults).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Erstellen Sie ein SharePoint-Projekt
 Erstellen Sie zunächst eine SharePoint-Projekt.  
  
#### <a name="to-create-a-sharepoint-project"></a>So erstellen Sie ein SharePoint-Projekt  
  
1. Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.  
  
2. Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3. Wählen Sie im Vorlagenbereich die **SharePoint 2010-Projekt** Vorlage.  
  
4. In der **Namen** geben **ProfileTest**, und wählen Sie dann die **OK** Schaltfläche.  
  
    Die **SharePoint Customization Wizard** angezeigt wird.  
  
5. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL der SharePoint-Server-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden Sie den Standardspeicherort (http://<em>Systemname</em>/) .  
  
6. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus.  
  
    Zurzeit können Sie Farmlösungsprofile erstellen. Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Wählen Sie die **Fertig stellen** Schaltfläche. Das Projekt wird im **Projektmappen-Explorer**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Fügen Sie eine Funktion und den Funktionsereignisempfänger hinzu
 Fügen Sie dem Projekt als Nächstes eine Funktion zusammen mit dem Ereignisempfänger für die Funktion hinzu. Dieser Ereignisempfänger enthält den Code, für den das Profil erstellt wird.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>So fügen Sie eine Funktion und den Funktionsereignisempfänger hinzu  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Features** Knoten, wählen Sie **Feature hinzufügen**, und behalten Sie den Standardwert für den Namen **Feature1**.  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignisempfänger hinzufügen**.  
  
     Dadurch wird der Funktion eine Codedatei mit verschiedenen auskommentierten Ereignishandlern hinzugefügt, und die Datei wird für die Bearbeitung geöffnet.  
  
3.  Fügen Sie in der Ereignisempfängerklasse die folgenden Variablendeklarationen hinzu.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Ersetzen Sie die `FeatureActivated`-Prozedur durch den folgenden Code.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Fügen Sie die folgende Prozedur unter dem `FeatureActivated`Verfahren.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt (**ProfileTest**), und wählen Sie dann **Eigenschaften**.  
  
7.  In der **Eigenschaften** Dialogfeld auf die **SharePoint** Registerkarte.  
  
8.  In der **aktive Bereitstellungskonfiguration** wählen **keine Aktivierung**.  
  
     Durch die Auswahl dieser Bereitstellungskonfiguration können Sie später die Funktion in SharePoint manuell aktivieren.  
  
9. Speichern Sie das Projekt.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Konfigurieren und Bereitstellen der SharePoint-Anwendung
 Da das SharePoint-Projekt nun bereit ist, können Sie es konfigurieren und für den SharePoint-Server bereitstellen.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>So konfigurieren und stellen Sie die SharePoint-Anwendung bereit  
  
1.  Auf der **analysieren** Menü wählen **Leistungs-Assistenten starten**.  
  
2.  Auf der Seite eins von der **Leistungs-Assistent**, lassen Sie die Methode der profilerstellung als **CPU-Sampling** , und wählen Sie die **Weiter** Schaltfläche.  
  
     Die anderen Profilerstellungsmethoden können in komplexeren Profilerstellungssituationen verwendet werden. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  Auf der Seite zwei von der **Leistungs-Assistent**, lassen Sie das profilziel **ProfileTest** , und wählen Sie die **Weiter** Schaltfläche.  
  
     Wenn eine Projektmappe über mehrere Projekte verfügt, werden sie in dieser Liste angezeigt.  
  
4.  Auf Seite drei von der **Leistungs-Assistent**Deaktivieren der **Profilerstellung für Ebeneninteraktion aktivieren** aus, und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Die Funktion „Profilerstellung für Ebeneninteraktion“ (Tier Interaction Profiling, TIP) ist für das Messen der Leistung von Anwendungen, die Datenbanken abfragen, sowie für das Anzeigen der Anzahl der Häufigkeit, wie oft eine Webseite angefordert wird, hilfreich. Da diese Daten für dieses Beispiel nicht erforderlich sind, aktivieren wir diese Funktion nicht.  
  
5.  Auf Seite vier von der **Leistungs-Assistent**, lassen Sie die **profilerstellung nach Abschluss des Assistenten starten** ausgewählt, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Der Assistent ermöglicht die anwendungsprofilerstellung auf dem Server, zeigt der **Leistungs-Explorer** Fenster erstellt, bereitgestellt und die SharePoint-Anwendung ausgeführt wird.  
  
## <a name="run-the-sharepoint-application"></a>Führen Sie die SharePoint-Anwendung
 Aktivieren Sie die Funktion in SharePoint, wodurch die Auslösung des `FeatureActivation`-Ereigniscodes ausgelöst wird.  
  
#### <a name="to-run-the-sharepoint-application"></a>So führen Sie die SharePoint-Anwendung aus  
  
1.  Öffnen Sie in SharePoint die **Websiteaktionen** Menü, und wählen Sie dann **Standorteinstellungen**.  
  
2.  In der **Websiteaktionen** wählen die **Websitefeatures verwalten** Link.  
  
3.  In der **Features** wählen die **aktivieren** neben **ProfileTest Feature1**.  
  
     Aufgrund der in der `FeatureActivated`-Funktion aufgerufenen Leerlaufschleife tritt eine Pause auf, wenn Sie dies vornehmen.  
  
4.  Auf der **Schnellstart** Leiste **listet** , und klicken Sie dann in der **listet** wählen **Ankündigungen**.  
  
     Beachten Sie, dass der Liste eine neue Ankündigung hinzugefügt wurde, aus der hervorgeht, dass die Funktion aktiviert wurde.  
  
5.  Schließen Sie die SharePoint-Website.  
  
     Nach dem Schließen von SharePoint der Profiler erstellt und zeigt ein Beispiel-Profilerstellungsbericht und speichert es als eine VSP-Datei in die **ProfileTest** Ordner des Projekts.  
  
## <a name="view-and-interpret-the-profile-results"></a>Anzeigen und Interpretieren der Ergebnisse des Profils
 Zeigen Sie nun nach der Ausführung und Profilerstellung der SharePoint-Anwendung die Testergebnisse an.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>Zum Anzeigen und Interpretieren der Ergebnisse des Profils
  
1.  In der **Funktionen, die meisten Einzelaufgaben durchführen** Abschnitt der Beispiel-Berichterstellungsberichts, beachten Sie, dass `TimeCounter` wird am oberen Rand der Liste.  
  
     Diese Position deutet darauf hin, dass es sich bei `TimeCounter` um eine der Funktionen mit der höchsten Anzahl an Beispielen gehandelt hat. Hierbei handelt es sich also um einen der größten Leistungsengpässe in der Anwendung. Diese Situation ist nicht überraschend, da dies für Demonstrationszwecke extra so entworfen wurde.  
  
2.  In der **Funktionen, die meisten Einzelaufgaben durchführen** Abschnitt der `ProcessRequest` Link, um die kostenverteilung für anzuzeigen die `ProcessRequest` Funktion.  
  
     In der **aufgerufenen Funktionen** Abschnitt `ProcessRequest`, beachten Sie, dass die **FeatureActiviated** aufgeführt ist als am häufigsten aufgerufene Funktion.  
  
3.  In der **aufgerufenen Funktionen** Abschnitt der **FeatureActivated** Schaltfläche.  
  
     In der **aufgerufenen Funktionen** Abschnitt **FeatureActivated**, `TimeCounter` aufgeführt ist als am häufigsten aufgerufene Funktion. In der **Funktionscodeansicht** Bereich, der hervorgehobene Code (`TimeCounter`) ist der Hotspot, und gibt an, wo die Korrektur erforderlich ist.  
  
4.  Schließen Sie den Beispiel-Profilerstellungsbericht.  
  
     Um den Bericht erneut zu einem beliebigen Zeitpunkt anzuzeigen, öffnen Sie die VSP-Datei in die **Leistungs-Explorer** Fenster.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Korrigieren Sie den Code und die Anwendung reprofile
 Beheben Sie nun nach Ermittlung der fehlerhaften Funktion in der SharePoint-Anwendung das Problem.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>So beheben Sie den Code und nehmen eine erneute Profilerstellung der Anwendung vor  
  
1.  Kommentieren Sie im Funktionsereignisempfänger-Code den `TimeCounter`-Methodenaufruf in `FeatureActivated` aus, um zu verhindern, dass er aufgerufen wird.  
  
2.  Speichern Sie das Projekt.  
  
3.  In **Leistungs-Explorer**, öffnen Sie den Ordner "Ziele" aus, und wählen Sie dann die **ProfileTest** Knoten.  
  
4.  Auf der **Leistungs-Explorer** Symbolleiste in der **Aktionen** Registerkarte die **Profilerstellung starten** Schaltfläche.  
  
     Wenn Sie eine der profilerstellungs-Eigenschaften vor dem erneute profilerstellung der Anwendung ändern möchten, wählen Sie möchten die **Leistungs-Assistenten starten** stattdessen die Schaltfläche.  
  
5.  Befolgen Sie die Anweisungen in der **Ausführen der SharePoint-Anwendung** Abschnitt weiter oben in diesem Thema.  
  
     Die Funktion sollte nun weitaus schneller aktiviert werden, da der Aufruf der Leerlaufschleife beseitigt wurde. Im Beispiel-Profilerstellungsbericht wird dies berücksichtigt.  
  
## <a name="see-also"></a>Siehe auch
 [Performance Explorer (Leistungs-Explorer)](/visualstudio/profiling/performance-explorer)   
 [Übersicht über Leistungssitzungen](/visualstudio/profiling/performance-session-overview)   
 [Einführung in die Leistungsprofilerstellung](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Aufspüren von Anwendungsengpässen mit Visual Studio-Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
