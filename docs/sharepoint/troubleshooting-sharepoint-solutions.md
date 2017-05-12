---
caps.handback.revision: 41
---
# Problembehandlung bei SharePoint-L&#246;sungen
  Die folgenden Probleme oder Warnungen können auftreten, wenn SharePoint\-Lösungen mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debuggers debuggt werden.  Weitere Informationen finden Sie unter [NIB: Debugging SharePoint 2007 Workflow Solutions](http://msdn.microsoft.com/de-de/3a5392f3-66f3-48be-956e-02de23fa6247).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Einschränkungen von Tokens in visuellen Sandkasten\-Webparts  
 Visuelle Webparts in Sandkastenlösungen können Standardtokens wie $SPUrl, die die SharePoint\-Laufzeit unterstützt, nicht verarbeiten.  Daher wird die URL nicht ausgelöst, und Sie können den Inhalt nicht in der Entwurfsansicht im visuellen Webpartdesigner anzeigen, wenn Sie wie im folgenden Beispiel in einem Skriptelement direkt auf ihn verweisen:  
  
```  
<script src=”<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Um diese Einschränkung zu umgehen und das Token aufzulösen, verweisen Sie mithilfe von Literalen darauf:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## Zeicheneinschränkungen in Namen von Projekten und Projektelementen  
 Namen von Projekten und Projektelementen dürfen nur Zeichen enthalten, die in einem Bereitstellungspfad in SharePoint 2010 gültig sind.  Andere Zeichen sind nicht zulässig.  
  
### Fehlermeldung  
 Fehlermeldung "Ungültige Zeichen"  
  
### Lösung  
 Verwenden Sie für Namen von SharePoint\-Projekte und \-Projektelemenen nur die folgenden Zeichen:  
  
-   Alphanumerische ASCII\-Zeichen  
  
-   Leerzeichen  
  
-   Punkt \(.\)  
  
-   Komma \(,\)  
  
-   Unterstrich \(\_\)  
  
-   Bindestrich \(\-\)  
  
-   Umgekehrter Schrägstrich \(\\\)  
  
 Wenn ein Projekt verpackt wird, überprüft eine Gültigkeitsprüfungsregel, ob die Eigenschaft "Bereitstellungspfad" bei jeder Datei, die bereitgestellt wird, nur diese gültigen Zeichen enthält.  
  
## Fehler beim Erstellen von benutzerdefinierten Feldern  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden benutzerdefinierte Felder in XML definiert.  Fehler können auftreten, wenn ein Feld nicht definiert ist oder mit einem bestimmten Format auf das Feld verwiesen wird.  
  
### Fehlermeldung  
 Fehlermeldung "Ungültige Zeichen" zur Verpackungszeit.  
  
### Lösung  
 Die ID für eine Felddefinition muss eine GUID sein, die von geschweiften Klammern umgeben ist, wie im folgenden Beispiel dargestellt:  
  
```  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Wie im folgenden Beispiel dargestellt, muss ein Feldverweis in einen Inhaltstyp mit dem leeren Elementformat \(\<FieldRef \/\>\) und nicht mit Start\-\/Endelementen \(\<FieldRef\>\<\/FieldRef\>\) definiert werden.  
  
```  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Wenn der XML\-Quellcode für das Feld falsch formatiert ist, eine ungültige XML\-Datei ist oder ein anderes ein Problem aufweist, tritt der Fehler "Cannot parse file" auf.  
  
## Neue, nicht englische Websitedefinitionen werden nach dem Bereitstellen nicht auf der Websiteerstellungsseite angezeigt  
 Nach dem Erstellen und Bereitstellen einer Sitedefinition mit einer nicht englischen Version von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(also einer Version, deren Gebietsschema\-[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] nicht "1033" lautet\) wird im Feld **Vorlagenauswahl** nicht die Registerkarte **SharePoint\-Anpassungen** angezeigt, und die neue Websitevorlage wird nicht auf der Seite **Neue SharePoint\-Website** angezeigt.  
  
### Fehlermeldung  
 Keine.  
  
### Lösung  
 Dieses Problem tritt aufgrund eines falschen Werts in der Eigenschaft **Pfad** für die Konfigurationsdatei der webtemp\-Websitedefinition \(beispielsweise "webtemp\_SiteDefinitionProject1.xml"\) auf.  Ändern Sie in der Eigenschaft **Pfad** für die webtemp\-Datei, die sich am Bereitstellungsort befindet, den Wert "1033" zur entsprechenden Gebietsschema\-[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  Soll also beispielsweise das Gebietsschema für Japanisch verwendet werden, ändern Sie den Wert zu "1041".  Weitere Informationen finden Sie auf der MSDN\-Website mit den [Microsoft\-Zuweisungen der Gebietsschema\-IDs](http://go.microsoft.com/fwlink/?LinkID=165561).  
  
## Fehler beim Bereitstellen eines Workflowprojekts auf einem unveränderten System  
 Dieses Problem tritt auf, wenn ein Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf einem unveränderten System bereitgestellt wird.  Ein unverändertes System ist ein Computer mit einer neuen Installation von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und SharePoint, aber ohne bereitgestellte Workflowprojekte.  
  
### Fehlermeldung  
 Die SharePoint\-Liste kann nicht gefunden werden: Workflowverlauf.  
  
### Lösung  
 Dieser Fehler tritt aufgrund einer fehlenden Workflowverlaufsliste auf.  Da es sich bei der Entwicklungsumgebung um ein unverändertes System handelt, sind keine Workflows bereitgestellt, und die Workflowverlaufsliste ist noch nicht vorhanden.  Öffnen Sie den Workflow\-Assistenten, um dieses Problem zu beheben. Dadurch wird die Workflowverlaufsliste erstellt.  
  
##### So starten Sie den Workflow\-Assistenten erneut  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den Workflowknoten aus.  
  
2.  Wählen Sie im Eigenschaftenfenster bei einer die oft ausgegebene Befehlszeilen  Eigenschaft, die eine Schaltfläche mit Auslassungspunkten \(…\) besitzt, die Schaltfläche mit den Auslassungspunkten aus.  
  
## Der Benutzer muss beim Debuggen die Anwendungsseite im Browser aktualisieren, um ein aktualisiertes Bild anzuzeigen  
 Wenn Sie eine SharePoint\-Lösung mit einer Anwendungsseite debuggen, die ein Steuerelement mit einem Bild \(beispielsweise ein [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]\-Bild\-Steuerelement\) enthält, muss die Seite im Browser aktualisiert werden, damit am Bild vorgenommene Änderungen angezeigt werden.  
  
## Fehler: Der Speicherort der Website ist nicht gültig.  
 Dieses Problem kann auftreten, wenn [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nicht installiert ist.  Es kann auch auftreten, wenn Sie für die SharePoint\-Website, die im Assistent zum Anpassen von SharePoint angegeben ist, nicht über Administratorzugriff verfügen.  
  
### Fehlermeldung  
  
-   Der Speicherort der SharePoint\-Site ist nicht gültig.  
  
### Lösung  
  
-   Installieren Sie [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Stellen Sie sicher, dass Sie über Administratorzugriff auf die SharePoint\-Website verfügen.  Weitere Informationen finden Sie im [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] Onlineartikel zum [Gewähren des Zugriffs auf die Portalwebsite](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## Das Webereignis für eine Websitelöschung tritt im Ereignisempfängerprojekt nicht ein  
 Wenn Sie ein Ereignisempfängerprojekt erstellen und Sie bestimmte Webereignisse auswählen, z. B. "eine Website wird gelöscht", tritt das Ereignis nie ein.  
  
### Fehlermeldung  
 Keine.  
  
### Lösung  
 Dieses Problem tritt auf, da der Funktionsbereich "Site" sein muss, um Ereignisse auf Websiteebene zu behandeln, der Standardfunktionsbereich für Ereignisempfängerprojekte ist jedoch "Internet".  Die betroffenen Webereignisse sind:  
  
-   Eine Website wird gelöscht \(WebDeleting\)  
  
-   Eine Website wurde gelöscht \(WebDeleted\)  
  
-   Eine Website wird verschoben \(WebMoving\)  
  
-   Eine Website wurde verschoben \(WebMoved\)  
  
 Zum Beheben des Problems ändern Sie den Funktionsbereich des Ereignisempfängers wie folgt:  
  
##### So ändern Sie den Funktionsbereich des Ereignisempfängers  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** die FEATURE\-Datei des Ereignisempfängers im **Funktions\-Designer**, indem Sie auf die Datei doppelklicken oder deren Kontextmenü öffnen und dann **Öffnen** auswählen.  
  
2.  Wählen Sie den Pfeil neben **Bereich**, und wählen Sie dann in der daraufhin angezeigten Liste **Site** aus.  
  
## Ein Bereitstellungsfehler tritt auf, nachdem der Name eines Bezeichners in einem Business Data Connectivity\-Modell\-Projekt geändert wurde  
 Dieses Problem tritt auf, wenn Sie den Bezeichnernamen einer Entität in einem Business Data Connectivity\-Modell \(BDC\-Modell\) ändern, und dann versuchen, die Projektmappe bereitzustellen.  
  
### Fehlermeldungen  
  
-   \<*model name*\> weist die folgenden Aktivierungsfehler für externe Inhaltstypen auf …  
  
-   Das IMetadataObject mit dem Namen '\<*model name*\>' enthält im Feld 'name' einen duplizierten Wert ...  
  
### Lösung  
 Um dieses Problem zu beheben, löschen Sie das Modell manuell, und stellen Sie anschließend die Projektmappe erneut bereit.  Sie können das Modell mit einem der folgenden Tools löschen:  
  
-   SharePoint 2010\-Zentraladministration.  Weitere Informationen finden Sie auf der Microsoft TechNet\-Website unter [Verwalten von BDC\-Modellen](http://go.microsoft.com/fwlink/?LinkID=181472).  
  
-   Windows PowerShell.  Durch Eingabe des Befehls **Remove\-SPBusinessDataCatalogModel** an der Eingabeaufforderung können Sie das Modell löschen.  Weitere Informationen finden Sie auf der Microsoft TechNet\-Website unter [Allgemeine Cmdlets \(SharePoint Server 2010\)](http://go.microsoft.com/fwlink/?LinkID=182375).  
  
## Fehler beim Versuch, einen visuelles Webpart in SharePoint anzuzeigen  
 Dieses Problem tritt auf, wenn die **Path**\-Eigenschaft des Benutzersteuerelements nicht mit der Zeichenfolge "CONTROLTEMPLATES\\" beginnt.  
  
### Fehlermeldungen  
  
-   Die Datei "\/\_CONTROLTEMPLATES\/*\<project name\>*\/*\<Web Part name\>*\/*\<user control name\>*.ascx" ist nicht vorhanden.  
  
-   Serverfehler in "\/" Anwendung.  
  
### Lösung  
  
##### So beheben Sie dieses Problem  
  
1.  Wählen Sie im **Projektmappen\-Explorer** die Benutzersteuerelementdatei mit der Dateinamenerweiterung ".ascx" aus.  
  
2.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
3.  Erweitern Sie im Fenster **Eigenschaften** den Knoten **Bereitstellungsort**.  
  
4.  Stellen Sie sicher, dass der Wert der **Path**\-Eigenschaft mit der Zeichenfolge "CONTROLTEMPLATES\\" beginnt.  
  
## Fehler beim Ausführen eines importierter wiederverwendbaren Workflows, der ein Aufgabenformularfeld enthält  
 Dieses Problem tritt auf, wenn Sie einen Workflow importieren, der ein Aufgabenformular enthält, das über ein Feld verfügt, und dann den neuen Workflow auf dem gleichen System ausführen, aus dem Sie ihn importiert haben.  
  
### Fehlermeldung  
 Fehler in Bereitstellungsschritt "Funktionen aktivieren": Das in der Funktion \[*Guid*\] definierte Feld mit ID \[*Guid*\] wurde in der aktuellen Websitesammlung oder einer Unterwebsite gefunden.  
  
### Lösung  
 Dieser Fehler ist das Ergebnis von Feld\-ID\-Konflikten, die auftreten, weil das Projekt "Wiederverwendbaren Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] keine Aufgabenformularfeld\-IDs ändert.  Wenn Sie einen importierten Workflow auf dem gleichen Server bereitstellen, der den ursprünglichen Workflow enthält, treten Feld\-ID\-Konflikte auf.  
  
 Um dieses Problem zu beheben, verwenden Sie die Funktion "Suchen und Ersetzen", um den Wert des Feld\-ID\-Attributs in allen importierten Workflowdateien zu ändern.  
  
## Fehler beim Ausführen einer umbenannten importierten Listeninstanz  
 Dieses Problem tritt auf, wenn Sie eine importierte Listeninstanz umbenennen und diese dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausführen.  
  
### Fehlermeldung  
 Buildfehler: Fehler Bereitstellungsschritt "Funktionen aktivieren": Die Datei "Template\\Features\\\[*import project* *feature* *name*\]\\Files\\Lists\\\[*old* *list name*\]\\Schema.xml" ist nicht vorhanden.  
  
### Lösung  
 Wenn Sie eine Listeninstanz importieren, wird der Datei "Elements.xml" der Listeninstanz ein Attribut namens "CustomSchema" hinzugefügt.  Die Datei "Elements.xml" schließt den Pfad einer benutzerdefinierten Datei "schema.xml" für die Listeninstanz ein.  Wenn Sie die Listeninstanz in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umbenennen, ändert sich der Bereitstellungspfad für die benutzerdefinierte Datei "schema.xml", der Pfadwert des CustomSchema\-Attributs wird jedoch nicht aktualisiert.  Als Ergebnis kann die Listeninstanz die Datei "schema.xml" im alten Pfad, der vom CustomSchema\-Attribut angegeben wird, nicht finden, wenn die Funktion aktiviert wird.  
  
 Um dieses Problem zu beheben, aktualisieren Sie den Pfad des Bereitstellungsspeicherorts der Datei "schema.xml" im CustomSchema\-Attribut.  
  
## SharePoint\-Debugsitzung wurde von IIS beendet  
 Dieses Problem tritt auf, wenn Sie einen Haltepunkt in einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Lösung festlegen, die Taste F5 drücken, um ihn auszuführen, und länger als 90 Sekunden bei einem Haltepunkt verweilen.  
  
### Fehlermeldung  
 Der Webserverprozess, der debuggt wurde, wurde von Internetinformationsdienste \(Internet Information Services, IIS\) beendet.  Sie können dieses Problem vermeiden, indem Sie die Ping\-Einstellungen des Anwendungspools in den Internetinformationsdiensten konfigurieren.  Weitere Informationen finden Sie in der Hilfe.  
  
### Lösung  
 Standardmäßig wartet der IIS\-Anwendungspool 90 Sekunden auf die Antwort einer Anwendung, bevor diese geschlossen wird.  Dieser Prozess wird als "Pingen" der Anwendung bezeichnet.  Um dieses Problem zu beheben, können Sie entweder die Wartezeit verlängern oder das Pingen der Anwendung komplett deaktivieren.  
  
##### So greifen Sie auf die IIS\-Einstellungen für den Anwendungspool zu  
  
1.  Öffnen Sie IIS\-Manager.  
  
2.  Erweitern Sie im Bereich **Verbindungen** den SharePoint\-Serverknoten, und wählen Sie dann den Knoten **Anwendungspools** aus.  
  
3.  Wählen Sie auf der Seite **Anwendungspools** den SharePoint\-Anwendungspool \(in der Regel "SharePoint \- 80"\) aus, und wählen Sie dann im Bereich **Aktionen** den Link **Erweiterte Einstellungen** aus.  
  
4.  Um die Wartezeit bis zu einem IIS\-Timeout zu verlängern, ändern Sie den Wert von **Maximale Ping\-Antwortzeit \(Sekunden\)** auf einen Wert, der größer als 90 Sekunden ist.  
  
5.  Legen Sie **Ping aktiviert** auf **False** fest, um das Pingen von IIS zu deaktivieren.  
  
## Automatisches Zurückziehen hinterlässt verwaiste Listeninstanz in SharePoint  
 Dieses Problem tritt auf, wenn Sie die folgenden Schritte ausführen:  
  
1.  Erstellen einer Listendefinition, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Listeninstanz hat.  
  
2.  Drücken Sie die Taste F5, um die Projektmappe auszuführen.  
  
3.  Beenden des Debugvorgangs oder Schließen der SharePoint\-Website.  
  
4.  Erneutes Öffnen der SharePoint\-Website und Öffnen der Listeninstanz.  
  
### Fehlermeldung  
 Serverfehler in "\/" Anwendung.  
  
### Lösung  
 Dies geschieht, weil die Funktion zum automatischen Zurückziehen die Lösung zurückzieht, nachdem Sie eine Debugsitzung einer SharePoint\-Lösung geschlossen haben.  Die Zurückziehen löscht die Listendefinition aus SharePoint, jedoch nicht die Instanz der Liste.  Die zugrunde liegende Listendefinition ist für die Listeninstanz erforderlich.  
  
 Stellen Sie zum Beheben dieses Problems die Projektmappe bereit, indem Sie in der Menüleiste **Erstellen** und dann **Bereitstellen** auswählen. \(Debuggen Sie nicht die Projektmappe, indem Sie die Taste F5 drücken.\) Löschen Sie dann die Listeninstanz in SharePoint.  
  
## Ursprüngliche SharePoint\-Lösung wird durch eine exportierte Version ersetzt  
 Wenn Sie eine SharePoint\-Lösung exportieren, die Projektmappe in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren und dann wieder auf der gleichen Website bereitstellen, von der sie exportiert wurde, wird die ursprüngliche SharePoint\-Lösung ersetzt.  Dieses Problem tritt nicht auf, wenn Sie die Projektmappe auf einem Server bereitstellen, auf dem die ursprüngliche Projektmappe nicht aktiviert ist.  
  
### Fehlermeldung  
 Keine.  
  
### Lösung  
 Um zu verhindern, dass eine Projektmappe auf der Website überschreiben wird, von der sie exportiert wurde, ändern Sie die GUIDS der SolutionID und der Funktions\-IDs aller importierten Funktionen im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projekt.  
  
## Fehler beim Starten vom Debuggen  
 Wenn Sie das Debuggen einer SharePoint\-Lösung in Visual Studio starten, erhalten Sie eine Fehlermeldung, dass Visual Studio die Datei "Web.config" nicht laden konnte, da der angegebene Schlüssel nicht im Wörterbuch vorhanden ist.  
  
### Fehlermeldung  
 Die Konfigurationsdatei "Web.config" konnte nicht geladen werden.  Überprüfen Sie die Datei auf falsch formatierte XML\-Elemente, und versuchen Sie es erneut.  Fehler: Der angegebene Schlüssel war im Wörterbuch nicht vorhanden.  
  
### Lösung  
 Um dieses Problem zu beheben, stellen Sie sicher, dass der Site\-URL\-Eigenschaftswert des SharePoint\-Projekts in Visual Studio eine Entsprechung für die URL findet, die der Standardzone für die alternativen Zugriffszuordnungen der Webanwendung zugewiesen wurde.  Sie können diesen Fehler nicht beheben, indem Sie eine andere Zone, z. B. Intranet, für die URL verwenden.  Die Site\-URL für das Projekt und die URL in der Standardzone müssen übereinstimmen.  Um auf alternative Zugriffszuordnungen zuzugreifen, öffnen Sie das Hilfsprogramm "SharePoint 2010\-Zentraladministration", wählen Sie den Link **Anwendungsverwaltung** aus, und wählen Sie dann unter **Webanwendungen** den Link **Alternative Zugriffszuordnungen konfigurieren** aus.  Weitere Informationen finden Sie unter [Erstellen von Zonen für Webanwendungen](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## Siehe auch  
 [Problembehandlung beim SharePoint-Packen und -Bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)  
  
  