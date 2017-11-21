---
title: "Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b2785e69bbfd6dff17f73b9840b88ad48454e0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-profiling-a-sharepoint-application"></a>Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Profilerstellungstools in Visual Studio gezeigt, um die Leistung einer SharePoint-Anwendung zu optimieren. Bei der Beispielanwendung handelt es sich um einen SharePoint-Funktionsereignisempfänger, der eine Leerlaufschleife enthält, welche die Leistung des Funktionsereignisempfängers reduziert. Der Visual Studio-Profiler ermöglicht es Ihnen, Auffinden und beseitigen die teuerste (langsamsten) Bestandteile des Projekts, auch bekannt als die *Langsamster Pfad*.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   [Hinzufügen eines Features und Funktionsereignisempfängers](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Konfigurieren und Bereitstellen der SharePoint-Anwendung](#BKMK_ConfigSharePointApp).  
  
-   [Ausführen der SharePoint-Anwendung](#BKMK_RunSPApp).  
  
-   [Anzeigen und Interpretieren der Profilerstellungsergebnisse](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="creating-a-sharepoint-project"></a>Erstellen eines SharePoint-Projekts  
 Erstellen Sie zunächst eine SharePoint-Projekt.  
  
#### <a name="to-create-a-sharepoint-project"></a>So erstellen Sie ein SharePoint-Projekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  Klicken Sie im Bereich "Vorlagen" Wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
4.  In der **Namen** geben **ProfileTest**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
5.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite Geben Sie die URL für die SharePoint-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden den Standardspeicherort (http://*Systemname*/) .  
  
6.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld.  
  
     Zurzeit können Sie Farmlösungsprofile erstellen. Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die **Fertig stellen** Schaltfläche. Das Projekt wird im **Projektmappen-Explorer**.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a>Hinzufügen eines Features und Funktionsereignisempfängers  
 Fügen Sie dem Projekt als Nächstes eine Funktion zusammen mit dem Ereignisempfänger für die Funktion hinzu. Dieser Ereignisempfänger enthält den Code, für den das Profil erstellt wird.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>So fügen Sie eine Funktion und den Funktionsereignisempfänger hinzu  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Funktionen** Knoten, wählen Sie **Funktion hinzufügen**, und lassen Sie den Namen des Standardwerts **Feature1**.  
  
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
  
5.  Fügen Sie die folgende Prozedur unter dem `FeatureActivated`Prozedur.  
  
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
  
7.  In der **Eigenschaften** Dialogfeld Wählen Sie die **SharePoint** Registerkarte.  
  
8.  In der **aktive Bereitstellungskonfiguration** wählen **keine Aktivierung**.  
  
     Durch die Auswahl dieser Bereitstellungskonfiguration können Sie später die Funktion in SharePoint manuell aktivieren.  
  
9. Speichern Sie das Projekt.  
  
##  <a name="BKMK_ConfigSharePointApp"></a>Konfigurieren und Bereitstellen der SharePoint-Anwendung  
 Da das SharePoint-Projekt nun bereit ist, können Sie es konfigurieren und für den SharePoint-Server bereitstellen.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>So konfigurieren und stellen Sie die SharePoint-Anwendung bereit  
  
1.  Auf der **analysieren** Menü wählen **Leistungs-Assistenten starten**.  
  
2.  Auf der Seite eins von der **Leistungs-Assistenten**, lassen Sie die Methode der profilerstellung bei **CPU-Sampling** , und wählen Sie die **Weiter** Schaltfläche.  
  
     Die anderen Profilerstellungsmethoden können in komplexeren Profilerstellungssituationen verwendet werden. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  Auf der Seite zwei von der **Leistungs-Assistenten**, lassen Sie das profilziel **ProfileTest** , und wählen Sie die **Weiter** Schaltfläche.  
  
     Wenn eine Projektmappe über mehrere Projekte verfügt, werden sie in dieser Liste angezeigt.  
  
4.  Auf Seite drei von der **Leistungs-Assistenten**Deaktivieren der **Profilerstellung für Ebeneninteraktion aktivieren** Kontrollkästchen, und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Die Funktion „Profilerstellung für Ebeneninteraktion“ (Tier Interaction Profiling, TIP) ist für das Messen der Leistung von Anwendungen, die Datenbanken abfragen, sowie für das Anzeigen der Anzahl der Häufigkeit, wie oft eine Webseite angefordert wird, hilfreich. Da diese Daten für dieses Beispiel nicht erforderlich sind, aktivieren wir diese Funktion nicht.  
  
5.  Auf Seite vier von der **Leistungs-Assistenten**, lassen Sie die **profilerstellung nach Abschluss des Assistenten starten** Kontrollkästchen ausgewählt ist, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Der Assistent ermöglicht die anwendungsprofilerstellung auf dem Server, zeigt der **Leistungs-Explorer** Fenster erstellt, bereitgestellt und die SharePoint-Anwendung ausgeführt wird.  
  
##  <a name="BKMK_RunSPApp"></a>Ausführen der SharePoint-Anwendung  
 Aktivieren Sie das Feature in SharePoint, wodurch die Auslösung des `FeatureActivation`-Ereigniscodes ausgelöst wird.  
  
#### <a name="to-run-the-sharepoint-application"></a>So führen Sie die SharePoint-Anwendung aus  
  
1.  Öffnen Sie in SharePoint die **Websiteaktionen** Menü, und wählen Sie dann **Standorteinstellungen**.  
  
2.  In der **Websiteaktionen** wählen Sie die **Websitefunktionen verwalten** Link.  
  
3.  In der **Funktionen** wählen Sie die **aktivieren** neben **ProfileTest Feature1**.  
  
     Aufgrund der in der `FeatureActivated`-Funktion aufgerufenen Leerlaufschleife tritt eine Pause auf, wenn Sie dies vornehmen.  
  
4.  Auf der **Schnellstart** -Menüleiste **listet** , und klicken Sie dann in der **listet** wählen Sie **Ankündigungen**.  
  
     Beachten Sie, dass der Liste eine neue Ankündigung hinzugefügt wurde, aus der hervorgeht, dass die Funktion aktiviert wurde.  
  
5.  Schließen Sie die SharePoint-Website.  
  
     Nach dem Schließen von SharePoint der Profiler erstellt und zeigt ein Beispiel-Profilerstellungsbericht und speichert es als eine VSP-Datei in die **ProfileTest** Ordner des Projekts.  
  
##  <a name="BKMK_ViewResults"></a>Anzeigen und Interpretieren der Profilerstellungsergebnisse  
 Zeigen Sie nun nach der Ausführung und Profilerstellung der SharePoint-Anwendung die Testergebnisse an.  
  
#### <a name="to-view-and-interpret-the-profiling-results"></a>So zeigen Sie die Profilerstellungsergebnisse an und interpretieren Sie sie  
  
1.  In der **Funktionen, die meisten Einzelaufgaben** Abschnitt der Beispiel-Berichterstellungsberichts, beachten Sie, dass `TimeCounter` im oberen Bereich der Liste ist.  
  
     Diese Position deutet darauf hin, dass es sich bei `TimeCounter` um eine der Funktionen mit der höchsten Anzahl an Beispielen gehandelt hat. Hierbei handelt es sich also um einen der größten Leistungsengpässe in der Anwendung. Diese Situation ist nicht überraschend, da dies für Demonstrationszwecke extra so entworfen wurde.  
  
2.  In der **Funktionen, die meisten Einzelaufgaben** Abschnitt der `ProcessRequest` Link, um die kostenverteilung für anzuzeigen die `ProcessRequest` Funktion.  
  
     In der **Funktionen aufgerufen** Abschnitt `ProcessRequest`, beachten Sie, dass die **FeatureActiviated** Funktion als am häufigsten aufgerufene Funktion aufgeführt ist.  
  
3.  In der **Funktionen aufgerufen** Abschnitt der **FeatureActivated** Schaltfläche.  
  
     In der **Funktionen aufgerufen** Abschnitt **FeatureActivated**die `TimeCounter` Funktion als am häufigsten aufgerufene Funktion aufgeführt ist. In der **Funktionscodeansicht** Bereich, der hervorgehobene Code (`TimeCounter`) ist der Hotspot und gibt an, in dem es Korrekturen Bedarf.  
  
4.  Schließen Sie den Beispiel-Profilerstellungsbericht.  
  
     Öffnen Sie zum Anzeigen des Berichts jederzeit wieder die VSP-Datei in die **Leistungs-Explorer** Fenster.  
  
## <a name="fixing-the-code-and-reprofiling-the-application"></a>Beheben des Codes und erneute Profilerstellung der Anwendung  
 Beheben Sie nun nach Ermittlung der fehlerhaften Funktion in der SharePoint-Anwendung das Problem.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>So beheben Sie den Code und nehmen eine erneute Profilerstellung der Anwendung vor  
  
1.  Kommentieren Sie im Funktionsereignisempfänger-Code den `TimeCounter`-Methodenaufruf in `FeatureActivated` aus, um zu verhindern, dass er aufgerufen wird.  
  
2.  Speichern Sie das Projekt.  
  
3.  In **Leistungs-Explorer**, öffnen Sie den Ordner "Ziele", und wählen Sie dann die **ProfileTest** Knoten.  
  
4.  Auf der **Leistungs-Explorer** Symbolleiste in der **Aktionen** Registerkarte, und wählen Sie die **Profilerstellung starten** Schaltfläche.  
  
     Der Profilerstellungsdaten Eigenschaften vor der erneute profilerstellung der Anwendung ändern, wählen ggf. die **Leistungs-Assistenten starten** stattdessen die Schaltfläche.  
  
5.  Befolgen Sie die Anweisungen in der **Ausführen der SharePoint-Anwendung** Abschnitt weiter oben in diesem Thema.  
  
     Die Funktion sollte nun weitaus schneller aktiviert werden, da der Aufruf der Leerlaufschleife beseitigt wurde. Im Beispiel-Profilerstellungsbericht wird dies berücksichtigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Performance Explorer (Leistungs-Explorer)](/visualstudio/profiling/performance-explorer)   
 [Übersicht über Leistungssitzungen](/visualstudio/profiling/performance-session-overview)   
 [Einführung in die Leistungsprofilerstellung](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Ermitteln von Anwendungsengpässen mit Visual Studio-Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  