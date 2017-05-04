---
title: "Walkthrough: Profiling a SharePoint Application | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, profiling"
  - "performance testing [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, performance testing"
  - "profiling [SharePoint development in Visual Studio]"
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Walkthrough: Profiling a SharePoint Application
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Profilerstellungstools in Visual Studio gezeigt, um die Leistung einer SharePoint\-Anwendung zu optimieren.  Bei der Beispielanwendung handelt es sich um einen SharePoint\-Funktionsereignisempfänger, der eine Leerlaufschleife enthält, welche die Leistung des Funktionsereignisempfängers reduziert.  Mit der Visual Studio\-Profilerstellung können Sie die teuersten \(langsamsten\) Bestandteile des Projekts, die auch als *langsamster Pfad* bezeichnet werden, auffinden und beseitigen.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   [Hinzufügen eines Features und Funktionsereignisempfängers](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Konfigurieren und Bereitstellen der SharePoint-Anwendung](#BKMK_ConfigSharePointApp).  
  
-   [Ausführen der SharePoint-Anwendung](#BKMK_RunSPApp).  
  
-   [Anzeigen und Interpretieren der Profilerstellungsergebnisse](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## Erstellen eines SharePoint\-Projekts  
 Erstellen Sie zunächst eine SharePoint\-Projekt.  
  
#### So erstellen Sie ein SharePoint\-Projekt  
  
1.  Wählen Sie auf der Menüleiste **Datei**, **Neu**, **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
2.  Erweitern Sie unter **Visual C\#** oder **Visual Basic** den Knoten **SharePoint**, und wählen Sie dann den Knoten **2010** aus.  
  
3.  Wählen Sie im Vorlagenbereich die Vorlage **SharePoint 2010\-Projekt** aus.  
  
4.  Geben Sie „ProfileTest“ im Feld **Name** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
5.  Geben Sie auf der Seite **Site und Sicherheitsebene für Debugging angeben** die URL für die SharePoint\-Serversite ein, auf der Sie die Sitedefinition debuggen möchten, oder verwenden Sie den standardmäßigen Speicherort \(http:\/\/*systemname*\/\).  
  
6.  Wählen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** das Optionsfeld **Als Farmlösung bereitstellen** aus.  
  
     Zurzeit können Sie Farmlösungsprofile erstellen.  Weitere Informationen über Sandkastenlösungen im Vergleich zu Farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die Schaltfläche **Fertig stellen** aus.  Das Projekt wird im **Projektmappen\-Explorer** angezeigt.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a> Hinzufügen eines Features und Funktionsereignisempfängers  
 Fügen Sie dem Projekt als Nächstes ein Feature zusammen mit dem Ereignisempfänger für das Feature hinzu.  Dieser Ereignisempfänger enthält den Code, für den das Profil erstellt wird.  
  
#### So fügen Sie ein Feature und den Funktionsereignisempfänger hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten für die Features aus. Wählen Sie die Option zum Hinzufügen des Features aus, und belassen Sie den Namen des Standardwerts **Feature1** unverändert.  
  
2.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignisempfänger hinzufügen** aus.  
  
     Dadurch wird dem Feature eine Codedatei mit verschiedenen auskommentierten Ereignishandlern hinzugefügt, und die Datei wird für die Bearbeitung geöffnet.  
  
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
  
4.  Ersetzen Sie die `FeatureActivated`\-Prozedur durch den folgenden Code.  
  
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
  
5.  Fügen Sie die folgende Prozedur unter der `FeatureActivated`\-Prozedur hinzu.  
  
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
  
6.  \(Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt \(**ProfileTest**\), und wählen Sie **Eigenschaften** aus.\)  
  
7.  Wählen Sie die Registerkarte **SharePoint** im Dialogfeld **Eigenschaften** aus.  
  
8.  Wählen Sie **Keine Aktivierung** in der Liste **Aktive Bereitstellungskonfiguration** aus.  
  
     Durch die Auswahl dieser Bereitstellungskonfiguration können Sie später das Feature in SharePoint manuell aktivieren.  
  
9. Speichern Sie das Projekt.  
  
##  <a name="BKMK_ConfigSharePointApp"></a> Konfigurieren und Bereitstellen der SharePoint\-Anwendung  
 Da das SharePoint\-Projekt nun bereit ist, können Sie es konfigurieren und für den SharePoint\-Server bereitstellen.  
  
#### So konfigurieren und stellen Sie die SharePoint\-Anwendung bereit  
  
1.  Wählen Sie im Menü **Analyse** die Option **Leistungs\-Assistenten starten** aus.  
  
2.  Belassen Sie auf der Seite eins von **Leistungs\-Assistent** die Methode der Profilerstellung bei **CPU\-Sampling**, und wählen Sie die Schaltfläche **Weiter** aus.  
  
     Die anderen Profilerstellungsmethoden können in komplexeren Profilerstellungssituationen verwendet werden.  Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).  
  
3.  Belassen Sie auf der Seite zwei von **Leistungs\-Assistent** das Profilziel bei **ProfileTest**, und wählen Sie die Schaltfläche **Weiter** aus.  
  
     Wenn eine Projektmappe über mehrere Projekte verfügt, werden sie in dieser Liste angezeigt.  
  
4.  Deaktivieren Sie auf Seite drei von **Leistungs\-Assistent** das Kontrollkästchen **Profilerstellung für Ebeneninteraktion aktivieren**, und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
     Das Feature Profilerstellung für Ebeneninteraktion \(Tier Interaction Profiling, TIP\) ist für das Messen der Leistung von Anwendungen, die Datenbanken abfragen, sowie für das Anzeigen der Anzahl der Häufigkeit, wie oft eine Webseite angefordert wird, hilfreich.  Da diese Daten für dieses Beispiel nicht erforderlich sind, aktivieren wir dieses Feature nicht.  
  
5.  Lassen Sie auf Seite vier von **Leistungs\-Assistent** das Kontrollkästchen **Profilerstellung nach Abschluss des Assistenten starten** aktiviert, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Der Assistent ermöglicht die Anwendungsprofilerstellung auf dem Server, zeigt das Fenster **Leistungs\-Explorer** an, erstellt die SharePoint\-Anwendung, stellt sie bereit und führt sie aus.  
  
##  <a name="BKMK_RunSPApp"></a> Ausführen der SharePoint\-Anwendung  
 Aktivieren Sie das Feature in SharePoint, wodurch die Auslösung des `FeatureActivation`\-Ereigniscodes ausgelöst wird.  
  
#### So führen Sie die SharePoint\-Anwendung aus  
  
1.  Öffnen Sie in SharePoint das Menü **Websiteaktionen**, und wählen Sie dann **Websiteeinstellungen** aus.  
  
2.  Wählen Sie in der Liste **Websiteaktionen** den Link **Websitefeatures verwalten**.  
  
3.  Wählen Sie in der Liste **Features** neben **ProfileTest Feature1** die Schaltfläche **Aktivieren** aus.  
  
     Aufgrund der in der `FeatureActivated`\-Funktion aufgerufenen Leerlaufschleife tritt eine Pause auf, wenn Sie dies vornehmen.  
  
4.  Wählen Sie **Listen** auf der Leiste **Schnellstart** aus. Wählen Sie anschließend **Ankündigungen** in der Liste **Listen** aus.  
  
     Beachten Sie, dass der Liste eine neue Ankündigung hinzugefügt wurde, aus der hervorgeht, dass das Feature aktiviert wurde.  
  
5.  Schließen Sie die SharePoint\-Website.  
  
     Nach dem Schließen von SharePoint wird mit der Profilerstellung ein Beispiel\-Profilerstellungsbericht erstellt und angezeigt. Dieser wird in einer VSP\-Datei im Ordner **ProfileTest** des Projekts gespeichert.  
  
##  <a name="BKMK_ViewResults"></a> Anzeigen und Interpretieren der Profilerstellungsergebnisse  
 Zeigen Sie nun nach der Ausführung und Profilerstellung der SharePoint\-Anwendung die Testergebnisse an.  
  
#### So zeigen Sie die Profilerstellungsergebnisse an und interpretieren Sie sie  
  
1.  Beachten Sie im Abschnitt **Funktionen mit den meisten einzelnen Aufgaben** des Beispiel\-Berichterstellungsberichts, dass sich `TimeCounter` nahezu ganz oben in der Liste befindet.  
  
     Diese Position deutet darauf hin, dass es sich bei `TimeCounter` um eine der Funktionen mit der höchsten Anzahl an Beispielen gehandelt hat. Hierbei handelt es sich also um einen der größten Leistungsengpässe in der Anwendung.  Diese Situation ist nicht überraschend, da dies für Demonstrationszwecke extra so entworfen wurde.  
  
2.  Wählen Sie im Abschnitt **Funktionen mit den meisten einzelnen Aufgaben** den Link `ProcessRequest` aus, um die Kostenverteilung für die Funktion `ProcessRequest` anzuzeigen.  
  
     Beachten Sie im Abschnitt **Aufgerufene Funktionen** für `ProcessRequest`, dass die Funktion **FeatureActiviated** als am häufigsten aufgerufene Funktion aufgeführt ist.  
  
3.  Wählen Sie im Abschnitt **Aufgerufene Funktionen** die Schaltfläche **FeatureActivated** aus.  
  
     Im Abschnitt **Aufgerufene Funktionen** für **FeatureActivated** wird die `TimeCounter`\-Funktion als die am häufigsten aufgerufene Funktion aufgelistet.  Im Bereich **Funktionscodeansicht** zeigt der hervorgehobene Code \(`TimeCounter`\) den Bereich an, in dem es Korrekturen bedarf.  
  
4.  Schließen Sie den Beispiel\-Profilerstellungsbericht.  
  
     Öffnen Sie zum erneuten Anzeigen des Berichts die VSP\-Datei im Fenster **Leistungs\-Explorer**.  
  
## Beheben des Codes und erneute Profilerstellung der Anwendung  
 Beheben Sie nun nach Ermittlung der fehlerhaften Funktion in der SharePoint\-Anwendung das Problem.  
  
#### So beheben Sie den Code und nehmen eine erneute Profilerstellung der Anwendung vor  
  
1.  Kommentieren Sie im Funktionsereignisempfänger\-Code den `TimeCounter`\-Methodenaufruf in `FeatureActivated` aus, um zu verhindern, dass er aufgerufen wird.  
  
2.  Speichern Sie das Projekt.  
  
3.  Öffnen Sie im **Leistungs\-Explorer** den Ordner „Ziele“, und wählen Sie dann den Knoten **ProfileTest** aus.  
  
4.  Wählen Sie auf der Symbolleiste **Leistungs\-Explorer** auf der Registerkarte **Aktionen** die Schaltfläche **Profilerstellung starten** aus.  
  
     Wenn Sie Profilerstellungseigenschaften vor dem erneuten Vornehmen der Profilerstellung der Anwendung ändern möchten, müssen Sie stattdessen die Schaltfläche **Leistungs\-Assistenten starten** auswählen.  
  
5.  Befolgen Sie die Anweisungen im Abschnitt **Ausführen der SharePoint\-Anwendung**, der sich weiter oben in diesem Thema befindet.  
  
     Das Feature sollte nun weitaus schneller aktiviert werden, da der Aufruf der Leerlaufschleife beseitigt wurde.  Im Beispiel\-Profilerstellungsbericht wird dies berücksichtigt.  
  
## Siehe auch  
 [Verwenden von Profilerstellungstools](../profiling/performance-explorer.md)   
 [Übersicht über Leistungssitzungen der Profilerstellungstools](../profiling/performance-session-overview.md)   
 [Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md)   
 [Ermitteln von Anwendungsengpässen mit der Visual Studio\-Profilerstellung](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  