---
title: Debuggen von SharePoint-Lösungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f53ca7f1a5e449d47a30a32967072f7220c159a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903152"
---
# <a name="debug-sharepoint-solutions"></a>Debuggen von SharePoint-Lösungen
  SharePoint-Lösungen können mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers gedebuggt werden. Beim Starten des Debuggens, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektdateien auf dem SharePoint-Server bereitgestellt, und klicken Sie dann eine Instanz der SharePoint-Website im Webbrowser geöffnet. In den folgenden Abschnitte wird erklärt, wie SharePoint-Anwendungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gedebuggt werden.  
  
-   [Aktivieren des Debuggings](#EnableDebug)  
  
-   [F5-Debugging und Bereitstellung](#Deployment)  
  
-   [SharePoint-Projektfunktionen](#Features)  
  
-   [Debuggen von Workflows](#Workflow)  
  
-   [Debuggen von Funktionsereignisempfängern](#FeatureEvents)  
  
-   [Erweiterte Debuginformationen aktivieren](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>Debuggen aktivieren
 Wenn Sie eine SharePoint-Lösung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstmals debuggen, werden Sie in einem Dialogfeld darauf hingewiesen, dass die Datei web.config nicht zum Aktivieren des Debuggens konfiguriert ist. (Die Datei web.config wird erstellt, wenn Sie SharePoint-Server installieren. Weitere Informationen finden Sie unter [arbeiten mit "Web.config"-Dateien](http://go.microsoft.com/fwlink/?LinkID=149266).) Das Dialogfeld bietet die Optionen, das Projekt entweder ohne Debugging auszuführen oder die Datei web.config so zu ändern, dass das Debuggen aktiviert wird. Wenn Sie die erste Option auswählen, wird das Projekt normal ausgeführt. Bei Auswahl der zweiten Option wird die Datei "web.config" für Folgendes konfiguriert:  
  
- Aktivieren der Aufrufliste (`CallStack="true"`)  
  
- Deaktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
- Aktivieren von Kompilierungsdebugging (`<compilation debug="true">`)  
  
  Die resultierende Datei web.config sieht wie folgt aus:  
  
```xml  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 Um die Änderungen zurückzusetzen, und deaktivieren Sie das Debuggen, ändern Sie das folgende [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in der Datei "Web.config":  
  
-   Deaktivieren der Aufrufliste (`CallStack="false"`)  
  
-   Aktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Deaktivieren von Kompilierungsdebugging (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>Prozess zum Debuggen und Bereitstellung von F5
 Wenn Sie das SharePoint-Projekt im Debugmodus ausführen, werden im SharePoint-Bereitstellungsprozess die folgenden Aufgaben ausgeführt:  
  
1. Die anpassbaren Befehle vor der Bereitstellung werden ausgeführt.  
  
2. Es wird eine Weblösungspaketdatei (.wsp) mithilfe von [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]-Befehlen erstellt. Die WSP-Datei enthält alle erforderlichen Dateien und Funktionen. Weitere Informationen finden Sie unter [Übersicht über Lösungen](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3. Wenn die SharePoint-Lösung eine Farmlösung ist, wird der [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]-Anwendungspool für die angegebene Website-[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] wiederverwendet. In diesem Schritt werden vom [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]-Arbeitsprozess gesperrte Dateien freigegeben.  
  
4. Wenn bereits eine frühere Version des Pakets vorhanden ist, wird die frühere Version der Funktionen und Dateien in der WSP-Datei zurückgenommen. In diesem Schritt werden die Funktionen deaktiviert, das Lösungspaket deinstalliert und anschließend das Lösungspaket auf dem SharePoint-Server gelöscht.  
  
5. Die aktuelle Version der Funktionen und Dateien in der WSP-Datei wird installiert. In diesem Schritt wird die Lösung auf dem SharePoint-Server hinzugefügt und installiert.  
  
6. Für Workflows wird die Workflowassembly installiert. Sie können den Speicherort ändern, indem Sie mit der *Assemblyspeicherort* Eigenschaft.  
  
7. Die Funktion des Projekts wird in SharePoint aktiviert, wenn der Gültigkeitsbereich Website oder Web ist. Funktionen in den Gültigkeitsbereichen Farm und WebApplication werden nicht aktiviert.  
  
8. Für Workflows, ordnet den Workflow der SharePoint-Bibliothek, Liste oder -Website, die Sie ausgewählt haben, in der **SharePoint Customization Wizard**.  
  
   > [!NOTE]  
   >  Diese Zuordnung tritt nur bei Auswahl **automatisch zuordnen. Workflow** im Assistenten.  
  
9. Die anpassbaren Befehle nach der Bereitstellung werden ausgeführt.  
  
10. Fügt der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger an den [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] Prozess (*w3wp.exe*). Wenn der Projekttyp Sie ändern kann die *Sandkastenlösung* Eigenschaft und ihr Wert wird festgelegt, um **"true"**, fügt der Debugger an einen anderen Prozess an (*SPUCWorkerProcess.exe*). Weitere Informationen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Der JavaScript-Debugger wird gestartet, wenn die SharePoint-Lösung eine Farmlösung ist.  
  
12. Die entsprechende Bibliothek, Liste oder Websiteseite wird im Webbrowser an.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zeigt nach der Ausführung der einzelnen Aufgaben eine Statusmeldung im Ausgabefenster an. Wenn eine Aufgabe nicht abgeschlossen werden kann, zeigt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Fehlermeldung im Fenster Fehlerliste an.  
  
## <a name="sharepoint-project-features"></a>SharePoint-Projektfunktionen
 Bei einer Funktion handelt es sich um eine portable und modulare Funktionseinheit, die das Ändern von Websites mithilfe von Websitedefinitionen vereinfacht. Es ist auch ein Paket mit [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS)-Elemente, die für einen bestimmten Gültigkeitsbereich aktiviert werden kann und Ihnen dabei hilft, Benutzer, die ein bestimmtes Ziel oder eine Aufgabe auszuführen. Vorlagen werden als Funktionen bereitgestellt.  
  
 Wenn Sie ein Projekt im Debugmodus ausführen, wird der Bereitstellungsprozess erstellt einen Ordner in der *Feature* Verzeichnis *%COMMONPROGRAMFILES%\Microsoft Shared\web Server extensions\14\TEMPLATE\FEATURES*. Funktionsnamen weisen das Format *Projektname*_Feature*x*, z. B. TestProject_Feature1.  
  
 Des Ordners der Projektmappe im Featureverzeichnis enthält eine *Featuredefinition* Datei und ein *Workflowdefinition* Datei. Die Funktionsdefinitionsdatei (Feature.xml) beschreibt die Dateien in des Projekts Prozessaktivierungsdienst-Feature Projektdefinitionsdatei (*"Elements.xml"*) wird die Projektvorlage beschrieben. *"Elements.xml"* finden Sie im **Projektmappen-Explorer**, aber "Feature.xml" wird generiert, wenn das Lösungspaket erstellt wird. Weitere Informationen zu diesen Dateien finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
## <a name="debug-workflows"></a>Debuggen von Workflows
 Wenn Sie Workflowprojekte debuggen, fügt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflowvorlage (abhängig von deren Typ) einer Bibliothek oder einer Liste hinzu. Sie können dann die Workflowvorlage manuell oder durch Hinzufügen oder Aktualisieren eines Elements starten. Anschließend können Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden, um den Workflow zu debuggen.  
  
> [!NOTE]
>  Wenn Sie Verweise auf andere Assemblys hinzufügen, stellen Sie sicher, dass diese Assemblys im globalen Assemblycache installiert werden ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Andernfalls tritt bei der Workflowlösung ein Fehler auf. Informationen zum Installieren von Assemblys finden Sie unter [Manuelles Starten eines Workflows in einem Dokument oder Element](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
 Der Workflow wird jedoch nicht vom Bereitstellungsprozess gestartet. Der Workflow muss von der SharePoint-Site gestartet werden. Der Workflow kann auch mithilfe einer Clientanwendung wie Microsoft Office Word 2010 oder mithilfe eines gesonderten serverseitigen Codes gestartet werden. Verwenden Sie eine der im angegebenen Ansätze der **SharePoint Customization Wizard**.  
  
 Wenn Sie beispielsweise angegeben haben, dass der Workflow manuell gestartet werden kann, starten Sie den Workflow direkt vom Element in der Bibliothek oder der Liste. Weitere Informationen zum manuellen Starten eines Workflows finden Sie unter [Manuelles Starten eines Workflows auf ein Dokumentelement](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
## <a name="debug-feature-event-receivers"></a>Debuggen von Funktionsereignisempfängern
 Wenn Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-SharePoint-Anwendung ausführen, werden deren Funktionen standardmäßig automatisch auf dem SharePoint-Server aktiviert. Dies verursacht jedoch Probleme beim Debuggen von Funktionsereignisempfängern; da Wenn eine Funktion, indem aktiviert wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sie in einem anderen Prozess als der Debugger ausgeführt wird. Dies bedeutet, dass einige Debugfunktionen, z. B. Haltepunkte, nicht ordnungsgemäß funktionieren.  
  
 Um die automatische Aktivierung des Features in SharePoint zu deaktivieren und ordnungsgemäße Debuggen von Funktionsereignisempfängern zu ermöglichen, legen Sie den Wert der des Projekts **aktive Bereitstellungskonfiguration** Eigenschaft **keine Aktivierung** vor dem Debuggen. Wenn Sie Ihre SharePoint-Anwendung dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuggen, aktivieren Sie die Funktion manuell in SharePoint. Um das Feature zu aktivieren, öffnen Sie die **Websiteaktionen** Menü in SharePoint **Standorteinstellungen**, wählen Sie die **Websitefunktionen verwalten** verknüpfen, und wählen Sie dann die **Aktivieren** Schaltfläche neben der Funktion, um weiterhin wie gewohnt debuggen.  
  
## <a name="enable-enhanced-debug-information"></a>Aktivieren einer erweiterten Debuginformationen
 Aufgrund der manchmal komplexen Interaktionen zwischen den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Prozess (devenv.exe), die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Hostprozess (*vssphost4.exe*), SharePoint, und der WCF-Ebene, und Diagnostizieren von Fehlern, die auftreten, während Erstellen, bereitstellen und So weiter können eine Herausforderung darstellen. Um Unterstützung beim Beheben solcher Fehler zu erhalten, können Sie erweiterte Debuginformationen aktivieren. Wechseln Sie hierzu in die Windows-Registrierung zum folgenden Registrierungsschlüssel:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 Wenn die "EnableDiagnostics" **REG_DWORD** Wert nicht bereits vorhanden ist, erstellen Sie ihn manuell. Legen Sie den Wert "EnableDiagnostics" auf "1".  
  
 Wenn dieser Schlüsselwert auf 1 bewirkt, dass Stack Ablaufverfolgungsinformationen in angezeigt werden die **Ausgabe** Projektsystemfehler auftreten, während Sie, im ausgeführt werden Fenster [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Legen Sie "EnableDiagnostics" wieder auf 0 fest oder löschen ihn, um erweiterte Debuginformationen zu deaktivieren.  
  
 Weitere Informationen zu anderen SharePoint-Registrierungsschlüsseln finden Sie unter [-Erweiterungen für SharePoint-Tools in Visual Studio Debuggen](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
