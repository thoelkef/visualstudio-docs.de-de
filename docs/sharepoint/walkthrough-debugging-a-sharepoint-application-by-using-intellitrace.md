---
title: "Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace"
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
  - "IntelliTrace [SharePoint-Entwicklung in Visual Studio]"
  - "Eigenständige Datenauflistung"
  - "SharePoint-Entwicklung in Visual Studio, IntelliTrace"
  - "Datenauflistung"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace
  Mit IntelliTrace können Sie SharePoint\-Lösungen einfacher debuggen.  Herkömmliche Debugger erstellen lediglich eine aktuelle Momentaufnahme der Lösung.  Sie können mithilfe von IntelliTrace jedoch in der Lösung aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind, überprüfen und zum Code navigieren.  
  
 Diese exemplarische Vorgehensweise veranschaulicht, wie ein SharePoint 2010\- oder ein SharePoint 2013\-Projekt in Visual Studio Ultimate debuggt wird, indem Sie Microsoft Monitoring Agent verwenden, um IntelliTrace\-Daten bereitgestellter Anwendungen zu sammeln.  Zum Analysieren dieser Daten muss Visual Studio Ultimate verwendet werden.  Dieses Projekt integriert einen Funktionsempfänger, der bei aktivierter Funktion der Liste "Aufgaben" eine Aufgabe und der Liste "Ankündigungen" eine Ankündigung hinzufügt.  Wenn die Funktion deaktiviert wird, wird die Aufgabe als abgeschlossen gekennzeichnet, und der Liste "Ankündigungen" wird eine zweite Ankündigung hinzugefügt.  Die Prozedur enthält jedoch einen logischen Fehler, der verhindert, dass das Projekt ordnungsgemäß ausgeführt wird.  Mit IntelliTrace können Sie den Fehler suchen und korrigieren.  
  
 **Betrifft:** Die Informationen in diesem Thema beziehen sich auf SharePoint 2010\- und SharePoint 2013\-Lösungen, die in Visual Studio erstellt wurden.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Einen Funktionsempfänger erstellen](#BKMK_CreateReceiver)  
  
-   [Dem Funktionsempfänger Code hinzufügen](#BKMK_AddCode)  
  
-   [Das Projekt testen](#BKMK_Test1)  
  
-   [Sammeln Sie IntelliTrace-Daten mithilfe von Microsoft Monitoring Agent.](#BKMK_CollectDiagnosticData)  
  
-   [Die SharePoint-Lösung debuggen und korrigieren](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint.  Siehe [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio Ultimate  
  
##  <a name="BKMK_CreateReceiver"></a> Einen Funktionsempfänger erstellen  
 Erstellen Sie zunächst ein leeres SharePoint\-Projekt mit einem Funktionsempfänger.  
  
#### So erstellen Sie einen Funktionsempfänger  
  
1.  Erstellen Sie eine SharePoint 2010\- oder SharePoint 2013\-Projektmappe mit Namen "IntelliTraceTest".  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt, in dem Sie die SharePoint\-Website für Ihr Projekt und die Vertrauensebene der Projektmappe angeben können.  
  
2.  Klicken Sie auf das Optionsfeld **Als Farmlösung bereitstellen** und dann auf **Fertig stellen**.  
  
     IntelliTrace kann nur für Farmlösungen verwendet werden.  
  
3.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **Funktionen**, und wählen Sie dann **Funktion hinzufügen** aus.  
  
     "Feature1.feature" wird angezeigt.  
  
4.  Öffnen Sie das Kontextmenü für "Feature1.feature", und wählen Sie dann **Ereignisempfänger hinzufügen**, um der Funktion ein Codemodul hinzuzufügen.  
  
##  <a name="BKMK_AddCode"></a> Dem Funktionsempfänger Code hinzufügen  
 Fügen Sie anschließend zwei Methoden im Funktionsempfänger Code hinzu: `FeatureActivated` und `FeatureDeactivating`.  Diese Methoden lösen immer dann aus, wenn eine Funktion in SharePoint aktiviert bzw. deaktiviert wird.  
  
#### So fügen Sie dem Funktionsempfänger Code hinzu  
  
1.  Fügen Sie am Anfang der `Feature1EventReceiver`\-Klasse den folgenden Code hinzu, um Variablen zu deklarieren, mit denen die SharePoint\-Website und \-Unterwebsite angegeben werden:  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  Ersetzen Sie die `FeatureActivated`\-Methode durch folgenden Code:  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
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
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  Ersetzen Sie die `FeatureDeactivating`\-Methode durch folgenden Code:  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> Das Projekt testen  
 Wenn dem Funktionsempfänger der Code hinzugefügt wurde und der Datensammler ausgeführt wird, stellen Sie die SharePoint\-Lösung bereit. Führen Sie sie aus, um die ordnungsgemäße Funktion zu testen.  
  
> [!IMPORTANT]  
>  In diesem Beispiel wird ein Fehler im Ereignishandler "FeatureDeactivating" ausgelöst.  Im weiteren Verlauf dieser exemplarischen Vorgehensweise suchen Sie diesen Fehler anhand der vom Datensammler erstellten .iTrace\-Datei.  
  
#### So testen Sie das Projekt  
  
1.  Stellen Sie die Lösung für SharePoint bereit, und öffnen Sie die SharePoint\-Website in einem Browser.  
  
     Die Funktion wird automatisch aktiviert. Dadurch wird bewirkt, dass der Funktionsempfänger eine Ankündigung und eine Aufgabe hinzufügt.  
  
2.  Zeigen Sie den Inhalt der Listen mit Ankündigungen und Aufgaben an.  
  
     In der Liste "Ankündigungen" sollte nun eine neue Ankündigung mit dem Namen **Activated feature: IntelliTraceTest\_Feature1** aufgeführt werden, und in der Liste "Aufgaben" eine neue Aufgabe mit dem Namen **Deactivate feature: IntelliTraceTest\_Feature1**.  Wenn eines der Elemente fehlt, überprüfen Sie, ob die Funktion aktiviert ist.  Aktivieren Sie sie andernfalls.  
  
3.  Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:  
  
    1.  Klicken Sie in SharePoint im Menü **Websiteaktionen** auf **Websiteeinstellungen**.  
  
    2.  Klicken Sie unter **Websiteaktionen** auf den Link **Websitefeatures verwalten**.  
  
    3.  Klicken Sie neben **IntelliTraceTest Feature1** auf die Schaltfläche **Deaktivieren**.  
  
    4.  Wählen Sie auf der Seite "Warnungen" den Link **Dieses Feature deaktivieren**.  
  
     Vom Ereignishandler "FeatureDeactivating\(\)" wird ein Fehler ausgelöst.  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Sammeln Sie IntelliTrace\-Daten mithilfe von Microsoft Monitoring Agent.  
 Wenn Sie Microsoft Monitoring Agent auf dem System installieren, auf dem SharePoint ausgeführt wird, können Sie SharePoint\-Lösungen debuggen, indem Sie spezifischere Daten verwenden, als die von IntelliTrace zurückgegebenen generischen Informationen.  Der Agent funktioniert außerhalb von Visual Studio, indem PowerShell\-Cmdlets verwendet werden, um Debuginformationen zu sammeln, während die SharePoint\-Lösung ausgeführt wird.  
  
> [!NOTE]  
>  Die Konfigurationsinformationen in diesem Abschnitt beziehen sich auf dieses Beispiel.  Weitere Informationen über andere Konfigurationsoptionen finden Sie unter [Verwenden des eigenständigen IntelliTrace-Collectors](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
1.  Auf dem Computer, der SharePoint ausführt, [Installieren Sie Microsoft Monitoring Agent und beginnen Sie, Ihre Lösung zu überwachen](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
2.  Deaktivieren Sie die Funktion:  
  
    1.  Klicken Sie in SharePoint im Menü **Websiteaktionen** auf **Websiteeinstellungen**.  
  
    2.  Klicken Sie unter **Websiteaktionen** auf den Link **Websitefeatures verwalten**.  
  
    3.  Klicken Sie neben **IntelliTraceTest Feature1** auf die Schaltfläche **Deaktivieren**.  
  
    4.  Wählen Sie auf der Seite "Warnungen" den Link **Dieses Feature deaktivieren**.  
  
     Ein Fehler tritt auf \(in diesem Fall aufgrund des Fehlers im Ereignishandler "FeatureDeactivating\(\)"\).  
  
3.  Im PowerShell\-Fenster führen Sie den Befehl [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) aus, um die ITRACE\-Datei zu erstellen, beenden Sie das Überwachen, und starten Sie die SharePoint\-Lösung neu.  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> Die SharePoint\-Lösung debuggen und korrigieren  
 Jetzt können Sie die IntelliTrace\-Protokolldatei in Visual Studio anzeigen, um den Fehler in der SharePoint\-Lösung zu suchen und zu beheben.  
  
#### So debuggen und korrigieren Sie die SharePoint\-Lösung  
  
1.  Öffnen Sie im Ordner "\\IntelliTraceLogs" die ITRACE\-Datei\-Datei in Visual Studio.  
  
     Die Seite **IntelliTrace\-Zusammenfassung** wird angezeigt.  Da es sich um einen Ausnahmefehler handelt, wird eine SharePoint\-Korrelations\-ID \(eine GUID\) im Ausnahmefehlerbereich des Abschnitts **Analyse** angezeigt.  Wählen Sie die Schaltfläche **Aufrufliste** aus, um die Aufrufliste anzuzeigen, in der der Fehler aufgetreten ist.  
  
2.  Wählen Sie die Schaltfläche **Debugausnahme** aus.  
  
     Wenn Sie dazu aufgefordert werden, laden Sie Symboldateien.  Im Fenster **IntelliTrace** wird angezeigt, dass die Ausnahme vom Typ "schwerwiegender Fehler" aufgetreten ist.  
  
     Wählen Sie die Ausnahme im IntelliTrace\-Fenster aus, um den Code mit dem Fehler anzuzeigen.  
  
3.  Beheben Sie den Fehler, indem Sie die SharePoint\-Lösung öffnen und die **throw**\-Anweisung am Anfang der Prozedur "FeatureDeactivating\(\)" auskommentieren oder entfernen.  
  
4.  Erstellen Sie die Projektmappe in Visual Studio neu, und stellen Sie sie dann erneut für SharePoint bereit.  
  
5.  Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:  
  
    1.  Klicken Sie in SharePoint im Menü **Websiteaktionen** auf **Websiteeinstellungen**.  
  
    2.  Klicken Sie unter **Websiteaktionen** auf den Link **Websitefeatures verwalten**.  
  
    3.  Klicken Sie neben **IntelliTraceTest Feature1** auf die Schaltfläche **Deaktivieren**.  
  
    4.  Wählen Sie auf der Seite "Warnungen" den Link **Dieses Feature deaktivieren**.  
  
6.  Öffnen Sie die Liste "Aufgaben", und überprüfen Sie, ob der Wert **Status** der Aufgabe "Deaktivieren" jetzt ordnungsgemäß auf "Abgeschlossen" gesetzt ist, und der Wert **% abgeschlossen** jetzt "100 %" beträgt.  
  
     Der Code wird jetzt ordnungsgemäß ausgeführt.  
  
## Siehe auch  
 [Überprüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [Verwenden von IntelliTrace](../debugger/intellitrace.md)   
 [Exemplarische Vorgehensweise: Überprüfen von SharePoint\-Code mithilfe von Komponententests](http://msdn.microsoft.com/de-de/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  