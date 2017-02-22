---
title: "Projekt-Modell-Kernkomponenten | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektmodelle, Objekte und Schnittstellen"
  - "Projektmodelle, Dienste"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Projekt-Modell-Kernkomponenten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die folgenden Tabellen erweitert im Projektmodell.  Die vorhandenen kurzen Beschreibungen der Tabellen der Schnittstellen und der Dienste identifiziert im Modell und Schnittstellen und Dienste bestimmten Objekten zugeordnet ist.  Darüber hinaus werden die Tabellen einzeln anderen Schnittstellen aufgeführt, die in der Projekterstellung und Wartung abhängig von den Anforderungen des speziellen Projekttyps sind optional.  
  
 Weitere Informationen finden Sie unter [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### Paket \- Objekt  
  
|Schnittstelle|Kommentare|  
|-------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialisiert ein VSPackage in der IDE und macht seine Dienste für die IDE verfügbar.|  
  
### Projekt\-Factory Objekt  
  
|Schnittstelle|Kommentare|  
|-------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Verwaltet das Erstellen neuer Projekte und das Öffnen von vorhandenen Projekten.|  
  
### Projektobjekte  
  
|Schnittstellen|Kommentare|  
|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Verwaltet das Hinzufügen und Entfernen von Projektelementen, öffnet Editoren und behält moniker Zuordnung zwischen den einzelnen Dokumenten und `VSITEMID`bei.  Erbt von `IVsProject` und `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Verwaltet Navigations\- und Anzeigeeigenschaften und stellt Ereignisse bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Aktiviert die Ausführung des Befehls, die der von `IOleCommandTarget` für Befehle Ausschneiden und ist ähnlich wie die Umbenennen, gelten nur dann, wenn der Fokus im Projektmappen\-Explorer ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fungiert als die primäre Befehlsziel Oberfläche für eine Projekthierarchie.  Es handelt sich um die Standardschnittstelle zum Abfragen von Objekten für den Befehlsstatus oder Zustand und ausgeführten Befehle.  Verfügbar, wenn Sie im Fenster Projekt verwendet werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordiniert die Dauerhaftigkeit des Projekts zustandes.  In der Regel wird der Zustand gespeichert, kann jedoch als Projektdatei speichern systemen angepasst werden, die nicht dateibasierten sind.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Aktiviert das Projekt, um alle Aspekte der Persistenz für die zugehörigen Projektelemente, entweder als Dateien auf dem Datenträger oder Objekte in anderen Speicher systemen zu verwalten.  Die `IVsPeristHierarchyItem2`\-Schnittstelle wird für Elemente verwendet, die nicht die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>\-Schnittstelle implementieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordiniert Interaktionen mit Quellcodeverwaltung.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Aktiviert Projekte, Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Verwaltet Projektkonfiguration Objekte, z. B. Debug\- und Releasekonfigurationen.  Erstellen, Bereitstellen und Debugvorgänge werden durch Projektkonfiguration Objekte koordiniert.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Wird von Hierarchien, um die Löschung zu steuern \(destruktiv\) oder \(zerstörungsfreie\), Optionen für Hierarchien Elemente zu entfernen.  Rufen Sie Abfragen\-Schnittstelle auf der `IVsHierarchyDeleteHandler`\-Schnittstelle aus der `IVsHierarchy`\-Schnittstelle an.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Stellt die Option Implementierung des, des Objekts bereit, das die `IVsCfgProvider2`\-Schnittstelle auf einer anderen COM\-Identität als das Projektobjekt unterstützt, die die `IVsHierarchy`\-Schnittstelle implementiert.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Optionale Schnittstelle implementiert, um das Projekt erweiterbar von anderen Entwicklern zu machen.  Die `IVsProjectStartupServices`\-Schnittstelle ermöglicht einem Drittanbieter einem VSPackage, um eine GUID zu registrieren, das Sie in die Projektdatei, sodass jedes Mal, lädt das Projekt laden Sie den Dienst eines Drittanbieters GUID in die Projektdatei und führen den Aufruf `QueryService` für diesen GUID beibehalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Wird von Quellspalten hierarchien in einem `UIHierarchy` Fenster, um Vorgänge wie Ausschneiden und Kopieren in die Zwischenablage und Einfügen zu koordinieren.  Verwenden Sie die `AdviseClipboardHelperEvents` Zwischenablage Schnittstelle, um Ereignisse zu registrieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Stellt Informationen über ein gezogenes Element relativ zu dessen Datenquelle während eines Drag & Drop\-Vorgangs in einem Fenster Benutzeroberfläche\-Hierarchien bereit.  Wird von der `IVsHierarchy`\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Stellt Informationen über ein gezogenes Element relativ zum Ablageziel während eines Drag & Drop\-Vorgangs in einem Fenster Benutzeroberfläche\-Hierarchien bereit.  Wird von der `IVsHierarchy`\-Schnittstelle.|  
  
### Konfigurationsobjekt.  
  
|Schnittstellen|Kommentare|  
|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Stellt Informationen zu einer Konfiguration bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Aktiviert Projekte, Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Aktiviert ein Projekt mit Kontrolle des Debuggers ausgeführt werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Wird von Bereitstellungsprojekten, die Bereitstellungseigenschaften für andere Projekte Vorgänge ausführen.|  
  
### Konfigurations\-Generator Objekt  
  
|Schnittstellen|Kommentare|  
|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Verwaltet den Buildvorgang einer Projektkonfiguration.|  
  
### Zusätzliche Projektobjekte  
  
|Schnittstellen|Kommentare|  
|--------------------|----------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zeigt **Eigenschaften**\-Elementeigenschaften im Fenster angezeigt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zeigt Ausgaben für die Bereitstellung.|  
  
 In der folgenden Tabelle werden die kurze Beschreibungen der Dienste dar, die im Projektmodell identifiziert werden.  
  
### Dienste  
  
|Dienst|Kommentare|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Wird von VSPackages das Projekttypen implementieren, um zu registrieren, dass das Projekt factory mit der IDE vorhanden ist.  VSPackage muss `QueryService` für diesen Dienst aufrufen und die zugehörige Projekt factory registrieren, wenn `IVsPackage::SetSite`\-Methode aufgerufen wird.  Wenn die `SetSite`\-Methode nicht aufgerufen wird, wird das Projekt nicht instanziiert wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet Zugriff auf den internen IDE integrierten Konzept der aktuellen Projektmappe enthaltenen Projekte, z. B. die Fähigkeit, neue Projekte erstellt wird, listen erwähnt, Änderungen am Projekt usw.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wird von Projekten, die an der Quellcodeverwaltung teilnehmen möchten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Wartet, bis eine Tabelle aus geöffneten Dokumenten, um festzustellen, ob eines oder mehrere der Projektelemente bereits geöffnet sind.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Enthält den Schnittstellen und Methoden, die aufgerufen werden, um ein Projektelement mit dem Standardwert editors oder eines bestimmten Editors tatsächlich zu öffnen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Erforderlich, um alle Projekte aufgerufen werden soll, wenn sie Hinzufügen, Entfernen oder Umbenennen ihre Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Verwaltet Änderungen an einer Datei oder einem Verzeichnis und Clients benachrichtigt, wenn ausgewählte Dateien auf dem Datenträger geändert wurden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Erforderlich, von allen Projekten und Editoren aufgerufen werden, bevor sie modifizierte Elemente speichern oder sie.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Verwaltet die Reihenfolge der Vorgänge für Build und Bereitstellung Projektkonfigurationen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Ermöglicht den Zugriff auf Dienste Debugger auf niedriger Ebene, die für die meisten Steuerelemente Debuggen verwendet werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Aktiviert VSPackages\-Informationszugang über aktuelle Auswahl und ermöglicht die Kommunikation mit dem **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Stellt grundlegende Benutzeroberfläche\-verknüpfte IDE\-Funktionalität, z. B. die Fähigkeit, Tool\- oder Dokumentfenster zu erstellen oder ein Fehler aufzulisten und zu melden den Benutzer bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Ermöglicht den Zugriff auf die Statusleiste der IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Wird verwendet, um das Automatisierungsmodell zu implementieren.  Geben Sie im Projektmodell ein Properties\-Objekt zurück, mit dem Sie eine Instanz dieses Objekts erstellt wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Wird verwendet, um Ereignisse Zwischenablage auf dem Projektobjekt in der Hierarchie zu implementieren.  `SVsUIHierWinClipboardHelper` ordnungsgemäß können Sie Ausschneiden, Kopieren und Einfügen behandeln.|  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/de-de/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)