---
title: Problembehandlung beim SharePoint-Packen und-bereitstellen | Microsoft-Dokumentation
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
ms.openlocfilehash: 46cd388079db9d7869bcae733c6baef33c07a212
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53805132"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Problembehandlung bei SharePoint-Packen und-bereitstellen
  In diesem Thema werden verschiedene Probleme behandelt, die beim Packen und Bereitstellen von SharePoint-Lösungen auftreten können.

## <a name="enable-enhanced-debugging"></a>Aktivieren des erweiterten Debuggings
 Für die Diagnose zwischen Visual Studio, SharePoint und anderen Ebenen können Sie den Registrierungsschlüssel "EnableDiagnostics" verwenden und so die Stapelüberwachung anzeigen. Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Hinzufügen der Projektausgabe zum Lösungspaket
 Die Projektausgabe kann mithilfe des Paket-Designers einem Paket hinzugefügt werden. Vergewissern Sie sich jedoch beim Hinzufügen der Projektausgabe, dass die Plattform des Projekts der Plattform der SharePoint-Lösung entspricht. Wir empfehlen die Verwendung der **Any CPU** Zielplattform für die Assemblys, die auf einer SharePoint-Server bereitgestellt werden soll. Weitere Informationen finden Sie unter [Seite "Kompilieren", Projekt-Designer &#40;Visual Basic&#41; ](../ide/reference/compile-page-project-designer-visual-basic.md) und [erweiterten Dialogfeld Compilereinstellungen &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Schemavalidierungswarnungen und-Fehler
 Von den SharePoint-Entwicklungstools in Visual Studio werden Validierungsschritte ausgeführt, um die ordnungsgemäße Formatierung des Lösungspakets zu überprüfen. Sie können auch benutzerdefinierte Validierungsschritte für die Funktionen und die Pakete erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen, benutzerdefinierte Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Bereitstellungskonfliktlösung
 Beim Bereitstellen einer SharePoint-Lösung können sich unter Umständen Konflikte ergeben, wenn Elemente auf dem Server den gleichen Namen, die gleiche URL oder die gleiche ID besitzen wie ein Element im Lösungspaket. Sie können ändern, die **Bereitstellungskonfliktlösung** Eigenschaft zu beheben, melden oder Konflikte für Module, Webparts, Listeninstanzen und Inhaltstypen ignorieren.

 Die folgende Tabelle zeigt die Einstellungen für die **Bereitstellungskonfliktlösung** Eigenschaft.

|Wert|Beschreibung|
|-----------|-----------------|
|Automatisch|Erkennt Konflikte und löst die Konflikte automatisch.|
|Eingabeaufforderung|Erkennt Konflikte und meldet sie dem Entwickler vor dem Lösen der Konflikte.|
|Keine|Konflikte werden nicht erkannt.|

## <a name="differences-between-f5-deployment"></a>Unterschiede bei der F5-Bereitstellung
 Wenn Sie das SharePoint-Projekt mithilfe von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Testen und Debuggen auf dem lokalen SharePoint-Server bereitstellen, werden von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] einige zusätzliche Schritte ausgeführt.

1. Zurücksetzen von Internetinformationsdienste (IIS) während des Bereitstellungsschritts

2. Automatisches Zuordnen von Workflows

3. Festlegen der Funktionsaktivierungsreihenfolge anhand der Hierarchie im Paket-Designer

   Sie können benutzerdefinierte Bereitstellungsschritte hinzufügen, um weiteren Änderungen der **F5** Verhalten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Verzögertes Anzeigen der SharePoint-Seite bei der Bereitstellung visuelles Webpart
 Wird ein visuelles Webpart unter [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] im Ordner "Bin" bereitgestellt, dauert es sehr lang, bis die SharePoint-Seite angezeigt wird. Wenn Sie Dateien in einem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Verzeichnis der obersten Ebene (beispielsweise im Verzeichnis "Bin") ändern, wird die gesamte Webanwendung neu kompiliert. Dies kann dazu führen, dass die SharePoint-Seite mit einer Verzögerung von bis zu 25 Sekunden gerendert wird.

### <a name="error-message"></a>Fehlermeldung
 Keine

### <a name="resolution"></a>Auflösung
 Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen:

1.  Installieren Sie Update KB967535, wie in den Microsoft Support-Artikel beschrieben [zu beheben: Ein Hotfix ist verfügbar, die Behebung von zwei Problemen in ASP.NET in IIS 7.0 für Windows Vista und Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Fügen Sie der Datei "Web.config" die folgende Zeile hinzu:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint-projektbereitstellung schlägt fehl mit Fehler "Fehler beim Extrahieren der Cab-Datei in der Projektmappe"
 Wenn der Name eines SharePoint-Projektelements Klammern enthält, schlägt die Projektmappe mit einem Fehler bei der Bereitstellung fehl.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Fehler beim Extrahieren der Cab-Datei in der Projektmappe.

### <a name="resolution"></a>Auflösung
 Um dieses Problem zu umgehen, entfernen Sie alle Klammern in den Namen von SharePoint-Projektelementen.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Der Fehler tritt beim Bereitstellen eines visuellen Webparts auf einer Website eine andere Webanwendung
 Wenn Sie ein visuelles Webpart das erste Mal auf einer Website einer anderen Webanwendung als der bereitstellen, auf der es aktuell bereitgestellt ist (durch Ändern der SiteUrl-Eigenschaft des visuellen Webparts), wird ein Fehler ausgegeben.

### <a name="error-message"></a>Fehlermeldung
 Fehler im Bereitstellungsschritt "Lösung hinzufügen": Eine Funktion mit der ID [#] wurde bereits in dieser Farm installiert. Verwenden Sie das force-Attribut, um die Funktion explizit neu zu installieren.

### <a name="resolution"></a>Auflösung
 Dieser Fehler tritt aufgrund des Verfahrens auf, mit dem visuelle Webpartfunktionen in SharePoint zurückgenommen werden. Um das visuelle Webpart erfolgreich bereitzustellen, Bereitstellen der Lösung erneut durch Auswahl der **F5** Schlüssel.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Warnung wird angezeigt, beim Bereitstellen von geschachtelten Benutzersteuerelementen
 Diese Warnung wird ausgegeben, wenn Sie eine SharePoint-Lösung bereitstellen, die Benutzersteuerelemente geschachtelt hat, z. B. ein visuelles Webpart, das ein Benutzersteuerelement enthält, oder ein Benutzersteuerelement, das ein visuelles Webpart oder ein anderes Benutzersteuerelement enthält. Diese Warnung wird ausgegeben, wenn Sie ein Steuerelement in einen Designer aus der Toolbox ziehen oder mit Hinzufügen der @Register -Direktive in der Datenquellensicht.

### <a name="error-message"></a>Fehlermeldung
 Warnung 1 Element ' [*Steuerelementname*]' ist kein bekanntes Element. Dies kann auftreten, wenn es einen Kompilierungsfehler in der Website gibt, oder die Datei "web.config" fehlt.

### <a name="resolution"></a>Auflösung
 Wenn die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektsystem ist nicht von einem geschachtelten Benutzersteuerelement fähig, es kann keine IntelliSense-Funktionalität bereitstellen, und es wird eine Warnung ausgegeben. Das Projektsystem hat keine Kenntnis von einem geschachtelten Benutzersteuerelement, wenn das Projekt nicht erstellt wird und der Designer ist nicht geschlossen und erneut geöffnet werden, oder wenn die automatischen Zurückziehen aktiviert ist, die bewirkt, dass des Benutzersteuerelements aus der SharePoint-Struktur, die nach dem Debuggen zurückgezogen werden.

 Um diese Warnung zu entfernen, erstellen Sie entweder das Projekt und schließen und öffnen den Designer dann erneut, oder deaktivieren Sie für das Projekt die Option zum automatischen Zurückziehen. Deaktivieren Sie dazu die **nach Debuggen automatisch zurückziehen** auf das Kontrollkästchen der **SharePoint** Registerkarte im Dialogfeld Eigenschaften von Projekt.

## <a name="see-also"></a>Siehe auch

- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)