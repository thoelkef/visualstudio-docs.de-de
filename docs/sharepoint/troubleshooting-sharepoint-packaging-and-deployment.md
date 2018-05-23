---
title: Problembehandlung beim SharePoint-Packen und-bereitstellen | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22487077a355d51725258f37c03e5fd2bb58ab9b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>Problembehandlung beim SharePoint-Packen und -Bereitstellen
  In diesem Thema werden verschiedene Probleme behandelt, die beim Packen und Bereitstellen von SharePoint-Lösungen auftreten können.

## <a name="enabling-enhanced-debugging"></a>Aktivieren des erweiterten Debuggings
 Für die Diagnose zwischen Visual Studio, SharePoint und anderen Ebenen können Sie den Registrierungsschlüssel "EnableDiagnostics" verwenden und so die Stapelüberwachung anzeigen. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="adding-project-output-to-the-solution-package"></a>Hinzufügen der Projektausgabe zum Lösungspaket
 Die Projektausgabe kann mithilfe des Paket-Designers einem Paket hinzugefügt werden. Vergewissern Sie sich jedoch beim Hinzufügen der Projektausgabe, dass die Plattform des Projekts der Plattform der SharePoint-Lösung entspricht. Wir empfehlen die Verwendung der **Any CPU** Zielplattform für die Assemblys, die auf einer SharePoint-Server bereitgestellt werden soll. Weitere Informationen finden Sie unter [Seite "Kompilieren", Projekt-Designer &#40;Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) und [erweiterte Dialogfeld Compilereinstellungen &#40;Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).

## <a name="validation-warnings-and-errors"></a>Validierungswarnungen und -fehler
 Von den SharePoint-Entwicklungstools in Visual Studio werden Validierungsschritte ausgeführt, um die ordnungsgemäße Formatierung des Lösungspakets zu überprüfen. Sie können auch benutzerdefinierte Validierungsschritte für die Funktionen und die Pakete erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Bereitstellungskonfliktlösung
 Beim Bereitstellen einer SharePoint-Lösung können sich unter Umständen Konflikte ergeben, wenn Elemente auf dem Server den gleichen Namen, die gleiche URL oder die gleiche ID besitzen wie ein Element im Lösungspaket. Sie können ändern, die **Bereitstellungskonfliktlösung** Eigenschaft gelöst, gemeldet oder ignoriert werden Konflikte für Module, Webparts, Listeninstanzen und Inhaltstypen.

 Die folgende Tabelle enthält die Einstellungen für die **Bereitstellungskonfliktlösung** Eigenschaft.

|Wert|Beschreibung|
|-----------|-----------------|
|Automatisch|Erkennt Konflikte und löst die Konflikte automatisch.|
|Eingabeaufforderung|Erkennt Konflikte und meldet sie dem Entwickler vor dem Lösen der Konflikte.|
|Keiner|Konflikte werden nicht erkannt.|

## <a name="differences-between-f5-deployment"></a>Unterschiede bei der F5-Bereitstellung
 Wenn Sie das SharePoint-Projekt mithilfe von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Testen und Debuggen auf dem lokalen SharePoint-Server bereitstellen, werden von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] einige zusätzliche Schritte ausgeführt.

1.  Zurücksetzen von Internetinformationsdienste (IIS) während des Bereitstellungsschritts

2.  Automatisches Zuordnen von Workflows

3.  Festlegen der Funktionsaktivierungsreihenfolge anhand der Hierarchie im Paket-Designer

 Sie können benutzerdefinierte Bereitstellungsschritte hinzufügen, um das F5-Verhalten weiter anzupassen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>Verzögertes Anzeigen der SharePoint-Seite beim Bereitstellen eines visuellen Webparts
 Wird ein visuelles Webpart unter [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] im Ordner "Bin" bereitgestellt, dauert es sehr lang, bis die SharePoint-Seite angezeigt wird. Wenn Sie Dateien in einem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Verzeichnis der obersten Ebene (beispielsweise im Verzeichnis "Bin") ändern, wird die gesamte Webanwendung neu kompiliert. Dies kann dazu führen, dass die SharePoint-Seite mit einer Verzögerung von bis zu 25 Sekunden gerendert wird.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Auflösung
 Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen:

1.  Installieren Sie Update KB967535, wie in den Microsoft Support-Artikel beschriebenen [zu beheben: ein Hotfix ist verfügbar, die Behebung von zwei Problemen in ASP.NET in IIS 7.0 für Windows Vista und Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Fügen Sie der Datei "Web.config" die folgende Zeile hinzu:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Die SharePoint-Projektbereitstellung schlägt mit "Fehler beim Extrahieren der CAB-Datei in der Projektmappe" fehl
 Wenn der Name eines SharePoint-Projektelements Klammern enthält, schlägt die Projektmappe mit einem Fehler bei der Bereitstellung fehl.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Fehler beim Extrahieren der CAB-Datei in der Projektmappe.

### <a name="resolution"></a>Auflösung
 Um dieses Problem zu umgehen, entfernen Sie alle Klammern in den Namen von SharePoint-Projektelementen.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Beim Bereitstellen eines visuellen Webparts auf einer Website einer anderen Webanwendung wird ein Fehler angezeigt
 Wenn Sie ein visuelles Webpart das erste Mal auf einer Website einer anderen Webanwendung als der bereitstellen, auf der es aktuell bereitgestellt ist (durch Ändern der SiteUrl-Eigenschaft des visuellen Webparts), wird ein Fehler ausgegeben.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Eine Funktion mit der ID [#] wurde in dieser Farm bereits installiert. Verwenden Sie das force-Attribut, um die Funktion explizit neu zu installieren.

### <a name="resolution"></a>Auflösung
 Dieser Fehler tritt aufgrund des Verfahrens auf, mit dem visuelle Webpartfunktionen in SharePoint zurückgenommen werden. Um das visuelle Webpart erfolgreich bereitzustellen, stellen Sie die Projektmappe erneut bereit, indem Sie F5 drücken.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Beim Bereitstellen von geschachtelten Benutzersteuerelementen wird eine Warnung angezeigt
 Diese Warnung wird ausgegeben, wenn Sie eine SharePoint-Lösung bereitstellen, die Benutzersteuerelemente geschachtelt hat, z. B. ein visuelles Webpart, das ein Benutzersteuerelement enthält, oder ein Benutzersteuerelement, das ein visuelles Webpart oder ein anderes Benutzersteuerelement enthält. Diese Warnung wird ausgegeben, wenn Sie ein Steuerelement einem Designer durch ziehen es aus der Toolbox mit hinzufügen oder die @Register -Direktive in der Datenquellensicht an.

### <a name="error-message"></a>Fehlermeldung
 Warnung-1-Element "[*Steuerelementname*]" ist kein bekanntes Element. Dies kann auftreten, wenn es einen Kompilierungsfehler in der Website gibt, oder die Datei "web.config" fehlt.

### <a name="resolution"></a>Auflösung
 Wenn die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektsystem geschachteltes Benutzersteuerelement unbekannt ist, es kann keine IntelliSense zur Verfügung stellen und sie die Warnung ausgibt. Das Projektsystem hat keine Kenntnis von einem geschachtelten Benutzersteuerelement, wenn das Projekt nicht vordefiniert ist, und der Designer nicht geschlossen und erneut geöffnet wird oder wenn die automatischen Zurückziehen aktiviert ist, die bewirkt, dass des Benutzersteuerelements, nach dem Debuggen von SharePoint-Struktur zurückgenommen werden.

 Um diese Warnung zu entfernen, erstellen Sie entweder das Projekt und schließen und öffnen den Designer dann erneut, oder deaktivieren Sie für das Projekt die Option zum automatischen Zurückziehen. Deaktivieren Sie hierzu die **nach Debuggen automatisch zurückziehen** Kontrollkästchen auf der **SharePoint** Registerkarte im Dialogfeld Eigenschaften für Project.

## <a name="see-also"></a>Siehe auch
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)


