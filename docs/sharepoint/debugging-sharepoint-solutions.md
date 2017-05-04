---
title: "Debuggen von SharePoint-L&#246;sungen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Debuggen"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Debuggen von SharePoint-L&#246;sungen
  SharePoint\-Lösungen können mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debuggers gedebuggt werden.  Wenn Sie mit dem Debuggen beginnen, stellt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektdateien auf dem SharePoint\-Server bereit und öffnet dann im Webbrowser eine Instanz der SharePoint\-Website.  In den folgenden Abschnitte wird erklärt, wie SharePoint\-Anwendungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gedebuggt werden.  
  
-   [Aktivieren des Debuggens](#EnableDebug)  
  
-   [F5\-Debugging und der Bereitstellungsprozess](#Deployment)  
  
-   [SharePoint\-Projektfunktionen](#Features)  
  
-   [Debuggen von Workflows](#Workflow)  
  
-   [Debuggen von Funktionsereignisempfängern](#FeatureEvents)  
  
-   [Aktivieren von erweiterten Debuginformationen](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Aktivieren des Debuggens  
 Wenn Sie eine SharePoint\-Lösung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstmals debuggen, werden Sie in einem Dialogfeld darauf hingewiesen, dass die Datei web.config nicht zum Aktivieren des Debuggens konfiguriert ist. \(Die Datei web.config wird erstellt, wenn Sie SharePoint\-Server installieren.  Weitere Informationen finden Sie unter [Arbeiten mit Web.config\-Dateien](http://go.microsoft.com/fwlink/?LinkID=149266).\) Das Dialogfeld bietet die Optionen, das Projekt entweder ohne Debugging auszuführen oder die Datei web.config so zu ändern, dass das Debuggen aktiviert wird.  Wenn Sie die erste Option auswählen, wird das Projekt normal ausgeführt.  Bei Auswahl der zweiten Option wird die Datei "web.config" für Folgendes konfiguriert:  
  
-   Aktivieren der Aufrufliste \(`CallStack="true"`\)  
  
-   Deaktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="Off" />`\)  
  
-   Aktivieren von Kompilierungsdebugging \(`<compilation debug="true">`\)  
  
 Die resultierende Datei web.config sieht wie folgt aus:  
  
```  
  
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
  
 Um die Änderungen zurückzusetzen und das Debuggen zu deaktivieren, ändern Sie das folgende [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in der Datei web.config:  
  
-   Deaktivieren der Aufrufliste \(`CallStack="false"`\)  
  
-   Aktivieren von benutzerdefinierten Fehlern in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="On" />`\)  
  
-   Deaktivieren von Kompilierungsdebugging \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> F5\-Debugging und der Bereitstellungsprozess  
 Wenn Sie das SharePoint\-Projekt im Debugmodus ausführen, werden im SharePoint\-Bereitstellungsprozess die folgenden Aufgaben ausgeführt:  
  
1.  Die anpassbaren Befehle vor der Bereitstellung werden ausgeführt.  
  
2.  Es wird eine Weblösungspaketdatei \(.wsp\) mithilfe von [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Befehlen erstellt.  Die WSP\-Datei enthält alle erforderlichen Dateien und Funktionen.  Weitere Informationen finden Sie in der [Übersicht über Lösungen](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Wenn die SharePoint\-Lösung eine Farmlösung ist, wird der [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]\-Anwendungspool für die angegebene Website\-[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] wiederverwendet.  In diesem Schritt werden vom [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]\-Arbeitsprozess gesperrte Dateien freigegeben.  
  
4.  Wenn bereits eine frühere Version des Pakets vorhanden ist, wird die frühere Version der Funktionen und Dateien in der WSP\-Datei zurückgenommen.  In diesem Schritt werden die Funktionen deaktiviert, das Lösungspaket deinstalliert und anschließend das Lösungspaket auf dem SharePoint\-Server gelöscht.  
  
5.  Die aktuelle Version der Funktionen und Dateien in der WSP\-Datei wird installiert.  In diesem Schritt wird die Lösung auf dem SharePoint\-Server hinzugefügt und installiert.  
  
6.  Für Workflows wird die Workflowassembly installiert.  Sie können den Speicherort mit der Eigenschaft *Assembly Location* ändern.  
  
7.  Die Funktion des Projekts wird in SharePoint aktiviert, wenn der Gültigkeitsbereich Website oder Web ist.  Funktionen in den Gültigkeitsbereichen Farm und WebApplication werden nicht aktiviert.  
  
8.  Bei Workflows wird der Workflow der SharePoint\-Bibliothek, der Liste oder der Website zugeordnet, die im **Assistenten zum Anpassen von SharePoint** ausgewählt wurde.  
  
    > [!NOTE]  
    >  Diese Zuordnung tritt nur auf, wenn Sie im Assistenten **Workflow automatisch zuordnen** ausgewählt haben.  
  
9. Die anpassbaren Befehle nach der Bereitstellung werden ausgeführt.  
  
10. Fügt den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debugger an den [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]\-Prozess \(w3wp.exe\) an.  Wenn der Projekttyp das Ändern der *Sandboxed Solution*\-Eigenschaft zulässt und der Wert auf **true** festgelegt wird, fügt der Debugger einen anderen Prozess \(SPUCWorkerProcess.exe\) an.  Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Der JavaScript\-Debugger wird gestartet, wenn die SharePoint\-Lösung eine Farmlösung ist.  
  
12. Die entsprechende Bibliothek, Liste oder Websiteseite wird im Webbrowser an.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zeigt nach der Ausführung der einzelnen Aufgaben eine Statusmeldung im Ausgabefenster an.  Wenn eine Aufgabe nicht abgeschlossen werden kann, zeigt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine Fehlermeldung im Fenster Fehlerliste an.  
  
##  <a name="Features"></a> SharePoint\-Projektfunktionen  
 Bei einer Funktion handelt es sich um eine portable und modulare Funktionseinheit, die das Ändern von Websites mithilfe von Websitedefinitionen vereinfacht.  Eine Funktion ist außerdem ein Paket aus WSS\-Elementen \([!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]\), das für einen bestimmten Gültigkeitsbereich aktiviert werden kann und Benutzer beim Erreichen eines bestimmten Ziels bzw. beim Ausführen einer Aufgabe unterstützt.  Vorlagen werden als Funktionen bereitgestellt.  
  
 Beim Ausführen eines Projekts im Debugmodus wird im Bereitstellungsprozess ein Ordner im Verzeichnis *feature* unter %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES erstellt.  Funktionsnamen weisen das Format *project name*\_Feature*x* auf, z. B. TestProject\_Feature1.  
  
 Der Ordner der Projektmappe im Featureverzeichnis beinhaltet eine Datei für *Featuredefinition* und eine Datei für *Workflowdefinition*.  Die Funktionsdefinitionsdatei \(Feature.xml\) beschreibt die Dateien in der Projektfunktion.In der Projektdefinitionsdatei \(Elements.xml\) wird die Projektvorlage beschrieben.  "Elements.xml" befindet sich im **Projektmappen\-Explorer**, "Feature.xml" wird jedoch beim Erstellen des Lösungspakets generiert.  Weitere Informationen zu diesen Dateien finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Debuggen von Workflows  
 Wenn Sie Workflowprojekte debuggen, fügt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflowvorlage \(abhängig von deren Typ\) einer Bibliothek oder einer Liste hinzu.  Sie können dann die Workflowvorlage manuell oder durch Hinzufügen oder Aktualisieren eines Elements starten.  Anschließend können Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden, um den Workflow zu debuggen.  
  
> [!NOTE]  
>  Wenn Sie anderen Assemblys Verweise hinzufügen, stellen Sie sicher, dass diese Assemblys im globalen Assemblycache \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) installiert werden.  Andernfalls tritt bei der Workflowlösung ein Fehler auf.  Weitere Informationen zum Installieren von Assemblys finden Sie im Thema [Manuelles Starten eines Workflows für ein Dokument oder ein Element](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Der Workflow wird jedoch nicht vom Bereitstellungsprozess gestartet.  Der Workflow muss von der SharePoint\-Site gestartet werden.  Der Workflow kann auch mithilfe einer Clientanwendung wie Microsoft Office Word 2010 oder mithilfe eines gesonderten serverseitigen Codes gestartet werden.  Verwenden Sie einen der im **Assistenten zum Anpassen von SharePoint** angegebenen Ansätze.  
  
 Wenn Sie beispielsweise angegeben haben, dass der Workflow manuell gestartet werden kann, starten Sie den Workflow direkt vom Element in der Bibliothek oder der Liste.  Weitere Informationen zum manuellen Starten eines Workflows finden Sie unter [Manuelles Starten eines Workflows für ein Dokument oder ein Element](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Debuggen von Funktionsereignisempfängern  
 Wenn Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Anwendung ausführen, werden deren Funktionen standardmäßig automatisch auf dem SharePoint\-Server aktiviert.  Dies verursacht jedoch Probleme, wenn Sie Funktionsereignisempfänger debuggen, da eine von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktivierte Funktion in einem anderen Prozess ausgeführt wird als der Debugger.  Dies bedeutet, dass einige Debugfunktionen, z. B. Haltepunkte, nicht ordnungsgemäß funktionieren.  
  
 Um die automatische Aktivierung der Funktion in SharePoint zu deaktivieren und das ordnungsgemäße Debuggen von Funktionsereignisempfängern zu ermöglichen, legen Sie vor dem Debuggen den Wert der Eigenschaft **Aktive Bereitstellungskonfiguration** des Projekts auf **Keine Aktivierung** fest.  Wenn Sie Ihre SharePoint\-Anwendung dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuggen, aktivieren Sie die Funktion manuell in SharePoint.  Klicken Sie zum Aktivieren der Funktion in SharePoint im Menü **Websiteaktionen** auf **Websiteeinstellungen**, klicken Sie auf den Link **Websitefeatures verwalten**, und klicken Sie dann neben der Funktion auf die Schaltfläche **Aktivieren**, um das Debuggen dann normal fortzusetzen.  
  
##  <a name="EnhancedDebug"></a> Aktivieren von erweiterten Debuginformationen  
 Aufgrund der manchmal komplexen Interaktionen zwischen dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Prozess \(devenv.exe\), dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Hostprozess \(vssphost4.exe\), SharePoint und der WCF\-Ebene kann das Diagnostizieren von Fehlern, die beim Erstellen, Bereitstellen usw. auftreten, schwierig sein.  Um Unterstützung beim Beheben solcher Fehler zu erhalten, können Sie erweiterte Debuginformationen aktivieren.  Wechseln Sie hierzu in die Windows\-Registrierung zum folgenden Registrierungsschlüssel:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 Wenn der **REG\_DWORD**\-Wert "EnableDiagnostics" nicht bereits vorhanden ist, erstellen Sie ihn manuell.  Legen Sie den “EnableDiagnostics”\-Wert auf "1" fest.  
  
 Wenn dieser Schlüsselwert auf 1 festgelegt wird, werden Stapelüberwachungsinformationen im Fenster **Ausgabe** angezeigt, wenn bei der Ausführung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektsystemfehler auftreten.  Legen Sie "EnableDiagnostics" wieder auf 0 fest oder löschen ihn, um erweiterte Debuginformationen zu deaktivieren.  
  
 Weitere Informationen zu anderen SharePoint\-Registrierungsschlüsseln finden Sie unter [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  