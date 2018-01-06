---
title: "Problembehandlung bei SharePoint-Lösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, troubleshooting
ms.assetid: d3c8a01c-8fac-40d0-bf9e-476901f1490a
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5454aa06d4256c6c5e9ee1a8aa9573377ce9abdb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-sharepoint-solutions"></a>Problembehandlung bei SharePoint-Lösungen
  Die folgenden Probleme oder Warnungen können auftreten, wenn SharePoint-Lösungen mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers debuggt werden. Weitere Informationen finden Sie unter [Debuggen von SharePoint 2007-Workflow-Projektmappen](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Einschränkungen von Tokens in visuellen Sandkasten-Webparts  
 Visuelle Webparts in Sandkastenlösungen können Standardtokens wie $SPUrl, die die SharePoint-Laufzeit unterstützt, nicht verarbeiten. Daher wird die URL nicht ausgelöst, und Sie können den Inhalt nicht in der Entwurfsansicht im visuellen Webpartdesigner anzeigen, wenn Sie wie im folgenden Beispiel in einem Skriptelement direkt auf ihn verweisen:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Um diese Einschränkung zu umgehen und das Token aufzulösen, verweisen Sie mithilfe von Literalen darauf:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Zeicheneinschränkungen in Namen von Projekten und Projektelementen  
 Namen von Projekten und Projektelementen dürfen nur Zeichen enthalten, die in einem Bereitstellungspfad in SharePoint 2010 gültig sind. Andere Zeichen sind nicht zulässig.  
  
### <a name="error-message"></a>Fehlermeldung  
 Fehlermeldung "Ungültige Zeichen".  
  
### <a name="resolution"></a>Auflösung  
 Verwenden Sie für Namen von SharePoint-Projekte und -Projektelemenen nur die folgenden Zeichen:  
  
-   Alphanumerische ASCII-Zeichen  
  
-   Leerzeichen  
  
-   Punkt (.)  
  
-   Komma (,)  
  
-   Unterstrich (_)  
  
-   Bindestrich (-)  
  
-   Umgekehrter Schrägstrich (\\)  
  
 Wenn ein Projekt verpackt wird, überprüft eine Validierungsregel, ob die Eigenschaft „Bereitstellungspfad“ bei jeder Datei, die bereitgestellt wird, nur diese gültigen Zeichen enthält.  
  
## <a name="errors-when-creating-custom-fields"></a>Fehler beim Erstellen von benutzerdefinierten Feldern  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden benutzerdefinierte Felder in XML definiert. Fehler können auftreten, wenn ein Feld nicht definiert ist oder mit einem bestimmten Format auf das Feld verwiesen wird.  
  
### <a name="error-message"></a>Fehlermeldung  
 Die Fehlermeldung "Ungültige Zeichen" zur Verpackungszeit.  
  
### <a name="resolution"></a>Auflösung  
 Die ID für eine Felddefinition muss eine GUID sein, die von geschweiften Klammern umgeben ist, wie im folgenden Beispiel dargestellt:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Wie im folgenden Beispiel wird gezeigt, muss ein Feldverweis in einen Inhaltstyp definiert werden, mit dem leeren Elementformat (\<FieldRef / >), nicht mithilfe von Start-/Endelementen (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Wenn der XML-Quellcode für das Feld falsch formatiert ist, eine ungültige XML-Datei ist oder ein anderes ein Problem aufweist, tritt der Fehler "Cannot parse file" auf.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Neue, nicht englische Websitedefinitionen werden nach dem Bereitstellen nicht auf der Websiteerstellungsseite angezeigt  
 Nach dem Erstellen und einer Sitedefinition Bereitstellen mit einer nicht englischen Version von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (d. h. eine Version mit einem anderen Gebietsschema [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] als 1033), wird die **SharePoint-Anpassungen** Registerkarte nicht angezeigt, in der **Vorlagenauswahl** Feld und die neue Websitevorlage wird nicht angezeigt, der **neue SharePoint-Website** Seite.  
  
### <a name="error-message"></a>Fehlermeldung  
 Keine  
  
### <a name="resolution"></a>Auflösung  
 Dieses Problem tritt aufgrund eines falschen Werts in der **Pfad** -Eigenschaft für die Konfigurationsdatei der Webtemp-Websitedefinition (beispielsweise "webtemp_SiteDefinitionProject1.Xml. In der **Pfad** -Eigenschaft für die Webtemp-Datei befindet sich unter dem **Bereitstellungsspeicherort**, ändern "1033" zur entsprechenden Gebietsschema- [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Z. B. zum Verwenden einer japanischen Gebietsschema ändern Sie den Wert auf 1041. Weitere Informationen finden Sie unter [von Microsoft zugewiesene Gebietsschema-IDs](http://go.microsoft.com/fwlink/?LinkID=165561) auf der MSDN-Website.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Fehler beim Bereitstellen eines Workflowprojekts auf einem unveränderten System  
 Dieses Problem tritt auf, wenn ein Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf einem unveränderten System bereitgestellt wird. Ein unverändertes System ist ein Computer mit einer neuen Installation von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und SharePoint, aber ohne bereitgestellte Workflowprojekte.  
  
### <a name="error-message"></a>Fehlermeldung  
 Die SharePoint-Liste kann nicht gefunden werden: Workflowverlauf.  
  
### <a name="resolution"></a>Auflösung  
 Dieser Fehler tritt aufgrund einer fehlenden Workflowverlaufsliste auf. Da es sich bei der Entwicklungsumgebung um ein unverändertes System handelt, sind keine Workflows bereitgestellt, und die Workflowverlaufsliste ist noch nicht vorhanden. Öffnen Sie den Workflow-Assistenten, um dieses Problem zu beheben. Dadurch wird die Workflowverlaufsliste erstellt.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>So starten Sie den Workflow-Assistenten erneut  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Knoten "Workflow".  
  
2.  In der **Eigenschaften** Fenster, wählen Sie die Schaltfläche mit den Auslassungspunkten (...), auf eine Eigenschaft, die eine Auslassungszeichen-Schaltfläche verfügt.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Der Benutzer muss beim Debuggen die Anwendungsseite im Browser aktualisieren, um ein aktualisiertes Bild anzuzeigen  
 Wenn Sie eine SharePoint-Lösung mit einer Anwendungsseite debuggen, die ein Steuerelement mit einem Bild (beispielsweise ein [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]-Bild-Steuerelement) enthält, muss die Seite im Browser aktualisiert werden, damit am Bild vorgenommene Änderungen angezeigt werden.  
  
## <a name="error-the-site-location-is-not-valid"></a>Fehler: Der Speicherort der Website ist nicht gültig.  
 Dieses Problem kann auftreten, wenn [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nicht installiert ist. Sie kann auch auftreten, wenn Sie auf der SharePoint-Website, die in angegeben ist, nicht über Administratorzugriff verfügen die **Assistent zum Anpassen von SharePoint**.  
  
### <a name="error-message"></a>Fehlermeldung  
  
-   Der Speicherort der SharePoint-Site ist nicht gültig.  
  
### <a name="resolution"></a>Auflösung  
  
-   Installieren Sie [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Stellen Sie sicher, dass Sie über Administratorzugriff auf die SharePoint-Website verfügen. Weitere Informationen finden Sie unter der [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] Online Artikel [Gewähren von Zugriff auf die Portalwebsite](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Das Webereignis für eine Websitelöschung tritt im Ereignisempfängerprojekt nicht ein  
 Wenn Sie ein Ereignisempfängerprojekt erstellen und Sie bestimmte Webereignisse auswählen, z. B. "eine Website wird gelöscht", tritt das Ereignis nie ein.  
  
### <a name="error-message"></a>Fehlermeldung  
 Keine  
  
### <a name="resolution"></a>Auflösung  
 Dieses Problem tritt auf, da der Funktionsbereich "Site" sein muss, um Ereignisse auf Websiteebene zu behandeln, der Standardfunktionsbereich für Ereignisempfängerprojekte ist jedoch "Internet". Die betroffenen Webereignisse sind:  
  
-   Eine Website wird gelöscht (WebDeleting)  
  
-   Eine Website wurde gelöscht (WebDeleted)  
  
-   Eine Website wird verschoben (WebMoving)  
  
-   Eine Website wurde verschoben (WebMoved)  
  
 Zum Beheben des Problems ändern Sie den Funktionsbereich des Ereignisempfängers wie folgt:  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>So ändern Sie den Funktionsbereich des Ereignisempfängers  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Ereignis Datei des Ereignisempfängers in der **Funktions-Designer** indem Sie auf die Datei doppelklicken oder öffnen dessen Kontextmenü auswählen und dann **Öffnen**.  
  
2.  Wählen Sie den Pfeil neben **Bereich**, und wählen Sie dann **Website** in der Liste, die angezeigt wird.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Ein Bereitstellungsfehler tritt auf, nachdem der Name eines Bezeichners in einem Business Data Connectivity-Modell-Projekt geändert wurde  
 Dieses Problem tritt auf, wenn Sie den Bezeichnernamen einer Entität in einem Business Data Connectivity-Modell (BDC-Modell) ändern, und dann versuchen, die Projektmappe bereitzustellen.  
  
### <a name="error-messages"></a>Fehlermeldungen  
  
-   \<*Modellname*> weist die folgenden Aktivierungsfehler für externe Inhaltstypen...  
  
-   Das IMetadataObject mit dem Namen "\<*Modellname*>' weist einen Wert im Feld"Name", die dupliziert werden...  
  
### <a name="resolution"></a>Auflösung  
 Um dieses Problem zu beheben, löschen Sie das Modell manuell, und stellen Sie anschließend die Projektmappe erneut bereit.  Sie können das Modell mit einem der folgenden Tools löschen:  
  
-   SharePoint 2010-Zentraladministration. Weitere Informationen finden Sie unter [BDC-Modell-Management](http://go.microsoft.com/fwlink/?LinkID=181472) auf der Microsoft TechNet-Website.  
  
-   Windows PowerShell. Sie können das Modell löschen, indem Sie diesen Befehl an der Eingabeaufforderung eingeben: **Remove-SPBusinessDataCatalogModel**. Weitere Informationen finden Sie unter [allgemeine Cmdlets (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) auf der Microsoft TechNet-Website.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Fehler beim Versuch, einen visuelles Webpart in SharePoint anzuzeigen  
 Dieses Problem tritt auf, wenn die **Pfad** -Eigenschaft des Benutzersteuerelements beginnt nicht mit der Zeichenfolge "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Fehlermeldungen  
  
-   Die Datei "/ _CONTROLTEMPLATES /*\<Projektname >*/*\<-Webpart-Name >*/*\<Benutzersteuerelement Name >*.ascx "ist nicht vorhanden.  
  
-   Serverfehler in "/" Anwendung.  
  
### <a name="resolution"></a>Auflösung  
  
##### <a name="to-resolve-this-issue"></a>So beheben Sie dieses Problem  
  
1.  In **Projektmappen-Explorer**, wählen Sie die Benutzersteuerelementdatei, deren Dateinamenerweiterung .ascx ist.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.  
  
3.  In der **Eigenschaften** Fenster, erweitern Sie die **Bereitstellungsspeicherort** Knoten.  
  
4.  Stellen Sie sicher, dass der Wert der **Pfad** -Eigenschaft beginnt mit der Zeichenfolge "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Fehler beim Ausführen eines importierter wiederverwendbaren Workflows, der ein Aufgabenformularfeld enthält  
 Dieses Problem tritt auf, wenn Sie einen Workflow importieren, der ein Aufgabenformular enthält, das über ein Feld verfügt, und dann den neuen Workflow auf dem gleichen System ausführen, aus dem Sie ihn importiert haben.  
  
### <a name="error-message"></a>Fehlermeldung  
 Fehler im Bereitstellungsschritt "Funktionen aktivieren": das Feld mit der Id [*Guid*] in der Funktion definierten [*Guid*] wurde in der aktuellen Websitesammlung oder einer Unterwebsite gefunden.  
  
### <a name="resolution"></a>Auflösung  
 Dieser Fehler ist das Ergebnis von Feld-ID-Konflikten, die auftreten, weil die Wiederverwendbaren Workflow importieren im Projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aufgabenformularfeld IDs werden nicht geändert. Wenn Sie einen importierten Workflow auf dem gleichen Server, die den ursprünglichen Workflow enthält bereitstellen, treten Feld-ID-Konflikten.  
  
 Um dieses Problem zu beheben, verwenden Sie die Funktion „Suchen und Ersetzen“, um den Wert des Feld-ID-Attributs in allen importierten Workflowdateien zu ändern.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Fehler beim Ausführen einer umbenannten importierten Listeninstanz  
 Dieses Problem tritt auf, wenn Sie eine importierte Listeninstanz umbenennen und diese dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausführen.  
  
### <a name="error-message"></a>Fehlermeldung  
 Fehler beim Erstellen: Fehler im Bereitstellungsschritt "Funktionen aktivieren": die Datei Template\Features\\[*Projekt importieren**Feature**Namen*] \Files\Lists \\[*alte**Listennamen*] \Schema.xml ist nicht vorhanden.  
  
### <a name="resolution"></a>Auflösung  
 Wenn Sie eine Listeninstanz importieren, wird der Datei "Elements.xml" der Listeninstanz ein Attribut namens "CustomSchema" hinzugefügt. Die Datei "Elements.xml" schließt den Pfad einer benutzerdefinierten Datei "schema.xml" für die Listeninstanz ein. Wenn Sie die Listeninstanz in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umbenennen, ändert sich der Bereitstellungspfad für die benutzerdefinierte Datei "schema.xml", der Pfadwert des CustomSchema-Attributs wird jedoch nicht aktualisiert. Als Ergebnis kann die Listeninstanz die Datei „schema.xml“ im alten Pfad, der vom CustomSchema-Attribut angegeben wird, nicht finden, wenn die Funktion aktiviert wird.  
  
 Um dieses Problem zu beheben, aktualisieren Sie den Pfad des Bereitstellungsspeicherorts der Datei "schema.xml" im CustomSchema-Attribut.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint-Debugsitzung wurde von IIS beendet  
 Dieses Problem tritt auf, wenn Sie einen Haltepunkt, in festlegen eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Lösung wählen Sie die F5-Taste, um diesen auszuführen und verbleibt dann an einem Haltepunkt länger als 90 Sekunden dauern.  
  
### <a name="error-message"></a>Fehlermeldung  
 Der Webserverprozess, der debuggt wurde, wurde von Internetinformationsdienste (Internet Information Services, IIS) beendet. Sie können dieses Problem vermeiden, indem Sie die Ping-Einstellungen des Anwendungspools in den Internetinformationsdiensten konfigurieren. Weitere Informationen finden Sie in der Hilfe.  
  
### <a name="resolution"></a>Auflösung  
 Standardmäßig wartet der IIS-Anwendungspool 90 Sekunden auf die Antwort einer Anwendung, bevor diese geschlossen wird. Dieser Prozess wird als "Pingen" der Anwendung bezeichnet. Um dieses Problem zu beheben, können Sie entweder die Wartezeit verlängern oder das Pingen der Anwendung komplett deaktivieren.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>So greifen Sie auf die IIS-Einstellungen für den Anwendungspool zu  
  
1.  Öffnen Sie IIS-Manager.  
  
2.  In der **Verbindungen** Bereich, erweitern Sie den SharePoint-Serverknoten, und wählen Sie dann die **Anwendungspools** Knoten.  
  
3.  Auf der **Anwendungspools** Seite, und wählen Sie den SharePoint-Anwendungspool (in der Regel "SharePoint - 80"), und dann auf die **Aktionen** Bereich, wählen Sie die **Erweiterte Einstellungen** Link.  
  
4.  Um die Wartezeit vor dem Timeout für IIS zu erhöhen, ändern Sie den Wert der **maximale Ping-Antwortzeit (Sekunden)** auf einen Wert, der größer als 90 Sekunden ist.  
  
5.  Legen Sie zum Deaktivieren der Pingen von IIS **Ping aktiviert** auf **"false"**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatisches Zurückziehen hinterlässt verwaiste Listeninstanz in SharePoint  
 Dieses Problem tritt auf, wenn Sie die folgenden Schritte ausführen:  
  
1.  Erstellen einer Listendefinition, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Listeninstanz hat.  
  
2.  Drücken Sie die Taste F5, um die Projektmappe auszuführen.  
  
3.  Beenden des Debugvorgangs oder Schließen der SharePoint-Website.  
  
4.  Erneutes Öffnen der SharePoint-Website und Öffnen der Listeninstanz.  
  
### <a name="error-message"></a>Fehlermeldung  
 Serverfehler in "/" Anwendung.  
  
### <a name="resolution"></a>Auflösung  
 Dies geschieht, weil die Funktion zum automatischen Zurückziehen die Lösung zurückzieht, nachdem Sie eine Debugsitzung einer SharePoint-Lösung geschlossen haben. Die Zurückziehen löscht die Listendefinition aus SharePoint, jedoch nicht die Instanz der Liste. Die zugrunde liegende Listendefinition ist für die Listeninstanz erforderlich.  
  
 Um dieses Problem zu beheben, bereitstellen die Projektmappe durch, auf der Menüleiste **erstellen**, **bereitstellen**. (Debuggen Sie nicht die Projektmappe, indem Sie die Taste F5 drücken.) Löschen Sie dann die Listeninstanz in SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Ursprüngliche SharePoint-Lösung wird durch eine exportierte Version ersetzt  
 Wenn Sie eine SharePoint-Lösung exportieren, die Projektmappe in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren und dann wieder auf der gleichen Website bereitstellen, von der sie exportiert wurde, wird die ursprüngliche SharePoint-Lösung ersetzt. Dieses Problem tritt nicht auf, wenn Sie die Projektmappe auf einem Server bereitstellen, auf dem die ursprüngliche Projektmappe nicht aktiviert ist.  
  
### <a name="error-message"></a>Fehlermeldung  
 Keine  
  
### <a name="resolution"></a>Auflösung  
 Um zu verhindern, dass eine Projektmappe auf der Website überschreiben wird, von der sie exportiert wurde, ändern Sie die GUIDS der SolutionID und der Funktions-IDs aller importierten Funktionen im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekt.  
  
## <a name="error-appears-when-debugging-starts"></a>Fehler beim Starten vom Debuggen  
 Wenn Sie das Debuggen einer SharePoint-Lösung in Visual Studio starten, erhalten Sie eine Fehlermeldung, dass Visual Studio die Datei "Web.config" nicht laden konnte, da der angegebene Schlüssel nicht im Wörterbuch vorhanden ist.  
  
### <a name="error-message"></a>Fehlermeldung  
 Die Konfigurationsdatei "Web.config" konnte nicht geladen werden. Überprüfen Sie die Datei auf falsch formatierte XML-Elemente, und versuchen Sie es erneut. Fehler: Der angegebene Schlüssel war im Wörterbuch nicht vorhanden.  
  
### <a name="resolution"></a>Auflösung  
 Um dieses Problem zu beheben, stellen Sie sicher, dass der Site-URL-Eigenschaftswert des SharePoint-Projekts in Visual Studio eine Entsprechung für die URL findet, die der Standardzone für die alternativen Zugriffszuordnungen der Webanwendung zugewiesen wurde. Sie können diesen Fehler nicht beheben, indem Sie eine andere Zone, z. B. Intranet, für die URL verwenden. Die Site-URL für das Projekt und die URL in der Standardzone müssen übereinstimmen. Um alternative zugriffszuordnungen zuzugreifen, öffnen Sie die SharePoint 2010-Zentraladministration, wählen Sie die **Anwendungsverwaltung** Link, und dann unter **Webanwendungen**, wählen Sie die  **Alternative zugriffszuordnungen konfigurieren** Link. Weitere Informationen finden Sie unter [Erstellen von Zonen für Webanwendungen](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung beim SharePoint-Packen und-bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Debuggen in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
