---
caps.handback.revision: 24
---
# Problembehandlung beim SharePoint-Packen und -Bereitstellen
  In diesem Thema werden verschiedene Probleme behandelt, die beim Packen und Bereitstellen von SharePoint\-Lösungen auftreten können.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Aktivieren des erweiterten Debuggings  
 Für die Diagnose zwischen Visual Studio, SharePoint und anderen Ebenen können Sie den Registrierungsschlüssel "EnableDiagnostics" verwenden und so die Stapelüberwachung anzeigen.  Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Hinzufügen der Projektausgabe zum Lösungspaket  
 Die Projektausgabe kann mithilfe des Paket\-Designers einem Paket hinzugefügt werden.  Vergewissern Sie sich jedoch beim Hinzufügen der Projektausgabe, dass die Plattform des Projekts der Plattform der SharePoint\-Lösung entspricht.  Verwenden Sie für die Assemblys, die Sie auf einem SharePoint\-Server bereitstellen möchten, nach Möglichkeit das Plattformziel **Beliebige CPU**.  Weitere Informationen finden Sie unter [Seite "Kompilieren", Projekt-Designer &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) und [Dialogfeld "Erweiterte Compilereinstellungen &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Validierungswarnungen und \-fehler  
 Von den SharePoint\-Entwicklungstools in Visual Studio werden Validierungsschritte ausgeführt, um die ordnungsgemäße Formatierung des Lösungspakets zu überprüfen.  Sie können auch benutzerdefinierte Validierungsschritte für die Funktionen und die Pakete erstellen.  Weitere Informationen finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Bereitstellungskonfliktlösung  
 Beim Bereitstellen einer SharePoint\-Lösung können sich unter Umständen Konflikte ergeben, wenn Elemente auf dem Server den gleichen Namen, die gleiche URL oder die gleiche ID besitzen wie ein Element im Lösungspaket.  Sie können die Eigenschaft **Bereitstellungskonfliktlösung** ändern, sodass Konflikte für Module, Webparts, Listeninstanzen und Inhaltstypen gelöst, gemeldet oder ignoriert werden.  
  
 Die folgende Tabelle enthält die Einstellungen für die Eigenschaft **Bereitstellungskonfliktlösung**:  
  
|Wert|**Beschreibung**|  
|----------|----------------------|  
|Automatisch|Erkennt Konflikte und löst die Konflikte automatisch.|  
|Eingabeaufforderung|Erkennt Konflikte und meldet sie dem Entwickler vor dem Lösen der Konflikte.|  
|Kein|Konflikte werden nicht erkannt.|  
  
## Unterschiede bei der F5\-Bereitstellung  
 Wenn Sie das SharePoint\-Projekt mithilfe von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Testen und Debuggen auf dem lokalen SharePoint\-Server bereitstellen, werden von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] einige zusätzliche Schritte ausgeführt.  
  
1.  Zurücksetzen von Internetinformationsdienste \(IIS\) während des Bereitstellungsschritts  
  
2.  Automatisches Zuordnen von Workflows  
  
3.  Festlegen der Funktionsaktivierungsreihenfolge anhand der Hierarchie im Paket\-Designer  
  
 Sie können benutzerdefinierte Bereitstellungsschritte hinzufügen, um das F5\-Verhalten weiter anzupassen.  Weitere Informationen finden Sie unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Verzögertes Anzeigen der SharePoint\-Seite beim Bereitstellen eines visuellen Webparts  
 Wird ein visuelles Webpart unter [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] im Ordner "Bin" bereitgestellt, dauert es sehr lang, bis die SharePoint\-Seite angezeigt wird.  Wenn Sie Dateien in einem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Verzeichnis der obersten Ebene \(beispielsweise im Verzeichnis "Bin"\) ändern, wird die gesamte Webanwendung neu kompiliert.  Dies kann dazu führen, dass die SharePoint\-Seite mit einer Verzögerung von bis zu 25 Sekunden gerendert wird.  
  
### Fehlermeldung  
 Keine.  
  
### Lösung  
 Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen:  
  
1.  Installieren Sie das Update KB967535 gemäß den Anweisungen im Microsoft Support\-Artikel [Update: Für die Behebung von zwei Problemen in ASP.NET unter IIS 7.0 für Windows Vista und Windows Server 2008 steht ein Hotfix zur Verfügung](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Fügen Sie der Datei "Web.config" die folgende Zeile hinzu:  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## Die SharePoint\-Projektbereitstellung schlägt mit "Fehler beim Extrahieren der CAB\-Datei in der Projektmappe" fehl  
 Wenn der Name eines SharePoint\-Projektelements Klammern enthält, schlägt die Projektmappe mit einem Fehler bei der Bereitstellung fehl.  
  
### Fehlermeldung  
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Fehler beim Extrahieren der CAB\-Datei in der Projektmappe.  
  
### Lösung  
 Um dieses Problem zu umgehen, entfernen Sie alle Klammern in den Namen von SharePoint\-Projektelementen.  
  
## Beim Bereitstellen eines visuellen Webparts auf einer Website einer anderen Webanwendung wird ein Fehler angezeigt  
 Wenn Sie ein visuelles Webpart das erste Mal auf einer Website einer anderen Webanwendung als der bereitstellen, auf der es aktuell bereitgestellt ist \(durch Ändern der SiteUrl\-Eigenschaft des visuellen Webparts\), wird ein Fehler ausgegeben.  
  
### Fehlermeldung  
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Eine Funktion mit der ID \[\#\] wurde in dieser Farm bereits installiert.  Verwenden Sie das force\-Attribut, um die Funktion explizit neu zu installieren.  
  
### Lösung  
 Dieser Fehler tritt aufgrund des Verfahrens auf, mit dem visuelle Webpartfunktionen in SharePoint zurückgenommen werden.  Um das visuelle Webpart erfolgreich bereitzustellen, stellen Sie die Projektmappe erneut bereit, indem Sie F5 drücken.  
  
## Beim Bereitstellen von geschachtelten Benutzersteuerelementen wird eine Warnung angezeigt  
 Diese Warnung wird ausgegeben, wenn Sie eine SharePoint\-Lösung bereitstellen, die Benutzersteuerelemente geschachtelt hat, z. B. ein visuelles Webpart, das ein Benutzersteuerelement enthält, oder ein Benutzersteuerelement, das ein visuelles Webpart oder ein anderes Benutzersteuerelement enthält.  Diese Warnung wird ausgegeben, wenn Sie einem Designer ein Steuerelement hinzufügen, indem Sie es in der Quellansicht von der Toolbox oder mit der @Register\-Direktive ziehen.  
  
### Fehlermeldung  
 Warnung\-1\-Element' \[*Control Name*\]' ist kein bekanntes Element.  Dies kann auftreten, wenn es einen Kompilierungsfehler in der Website gibt, oder die Datei "web.config" fehlt.  
  
### Lösung  
 Wenn das [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projektsystem kein geschachteltes Benutzersteuerelement beachtet, kann es kein IntelliSense zur Verfügung stellen, und es wird eine Warnung ausgegeben.  Das Projektsystem hat keine Kenntnis von einem geschachtelten Benutzersteuerelement, wenn das Projekt nicht erstellt wird und der Designer nicht geschlossen und erneut geöffnet wird, oder wenn die Option zum automatischen Zurückziehen aktiviert wird, was dazu führt, dass das Benutzersteuerelement nach Debugging von der SharePoint\-Struktur zurückgenommen wird.  
  
 Um diese Warnung zu entfernen, erstellen Sie entweder das Projekt und schließen und öffnen den Designer dann erneut, oder deaktivieren Sie für das Projekt die Option zum automatischen Zurückziehen.  Deaktivieren Sie dazu auf der Registerkarte **SharePoint** des Dialogfelds mit den Projekteigenschaften das Kontrollkästchen **Nach Debuggen automatisch zurückziehen**.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  