---
title: Projektmodell-Kernkomponenten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706540"
---
# <a name="project-model-core-components"></a>Hauptkomponenten eines Projektmodells
Die folgenden Tabellen erweitern das Projektmodell. Die Tabellen enthalten kurze Beschreibungen der im Modell identifizierten Schnittstellen und Dienste sowie der Schnittstellen und Dienste, die bestimmten Objekten zugeordnet sind. Darüber hinaus werden in den Tabellen andere Schnittstellen beschrieben, die bei der Projekterstellung und -wartung abhängig von den Anforderungen Ihres spezifischen Projekttyps optional sind.

 Weitere Informationen finden Sie unter [Unterstützen von Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Paketobjekt

|Schnittstelle|Kommentare|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialisiert ein VSPackage in der IDE und stellt seine Dienste der IDE zur Verfügung.|

### <a name="project-factory-object"></a>Project Factory-Objekt

|Schnittstelle|Kommentare|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Verwaltet das Erstellen neuer Projekte und das Öffnen vorhandener Projekte.|

### <a name="project-objects"></a>Projektobjekte

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Verwaltet das Hinzufügen und Entfernen von Projektelementen, öffnet Editoren und `VSITEMID`verwaltet die Zuordnung zwischen jedem Dokumentmoniker und dem . Erbt von `IVsProject` `IVsProject2`und .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Verwaltet Navigations- und Anzeigeeigenschaften und stellt Ereignisse bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Aktiviert die Befehlsausführung `IOleCommandTarget` ähnlich wie für Befehle wie Ausschneiden und Umbenennen, die nur gelten, wenn sich der Fokus im Projektmappen-Explorer befindet.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Dient als primäre Befehlszielschnittstelle für eine Projekthierarchie. Es ist die Standardschnittstelle für die Abfrage von Objekten für ihren Befehlsstatus oder Status und ausgeführte Befehle. Verfügbar, wenn Sie nicht im Projektfenster fokussiert sind.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordiniert die Persistenz des Projektstatus. In der Regel wird der Projektstatus als Projektdatei gespeichert, kann jedoch an Speichersysteme angepasst werden, die nicht dateibasiert sind.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Ermöglicht dem Projekt die Verwaltung aller Aspekte der Persistenz für seine Projektelemente, entweder als Dateien auf dem Datenträger oder als Objekte in anderen Speichersystemen. Die `IVsPersistHierarchyItem2` Schnittstelle wird für Elemente verwendet, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle nicht implementieren.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordiniert Interaktionen mit der Quellcodeverwaltung.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Ermöglicht Projekten die Verwaltung von Konfigurationsinformationen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Verwaltet Projektkonfigurationsobjekte, z. B. Debug-/Release-Konfigurationen. Build-, Bereitstellungs- und Debugvorgänge werden über Projektkonfigurationsobjekte koordiniert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementiert von Hierarchien, um die Löschoptionen (destruktiv) oder entfernen (nicht destruktiv) für Hierarchieelemente zu steuern. Rufen Sie die `IVsHierarchyDeleteHandler` Abfrageschnittstelle `IVsHierarchy` auf der Schnittstelle von der Schnittstelle aus auf.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Stellt die Implementierungsoption bereit, `IVsCfgProvider2` das Objekt zu verwenden, das die Schnittstelle `IVsHierarchy` in einer anderen COM-Identität unterstützt als das Projektobjekt, das die Schnittstelle implementiert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Optionale Schnittstelle implementiert, um Ihr Projekt von anderen Entwicklern erweiterbar zu machen. Die `IVsProjectStartupServices` Schnittstelle ermöglicht es einem VSPackage eines Drittanbieters, eine GUID zu registrieren, die Sie in Ihrer Projektdatei beibehalten, sodass Sie bei jedem Laden des Projekts die Dienst-GUID eines Drittanbieters in Ihre Projektdatei laden und diese GUID aufrufen. `QueryService`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Wird durch Quellhierarchien `UIHierarchy` in einem Fenster implementiert, um Zwischenablagevorgänge wie Ausschneiden, Kopieren und Einfügen zu koordinieren. Verwenden `AdviseClipboardHelperEvents` Sie die Schnittstelle, um Zwischenablageereignisse zu registrieren.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Stellt Informationen zu einem gezogenen Element relativ zu seiner Datenquelle während eines Drag-and-Drop-Vorgangs in einem UI-Hierarchiefenster bereit. Wird von `IVsHierarchy` der Schnittstelle aufgerufen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Stellt Informationen zu einem gezogenen Element relativ zu seinem Ablageziel während eines Drag-and-Drop-Vorgangs in einem UI-Hierarchiefenster bereit. Wird von `IVsHierarchy` der Schnittstelle aufgerufen.|

### <a name="configuration-object"></a>Konfigurationsobjekt

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Stellt Informationen zu einer Konfiguration bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Ermöglicht Projekten die Verwaltung von Konfigurationsinformationen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Ermöglicht die Ausführung eines Projekts unter der Kontrolle des Debuggers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementiert von Bereitstellungsprojekten, die Bereitstellungsvorgänge für andere Projekte ausführen.|

### <a name="configuration-builder-object"></a>Configuration Builder-Objekt

|Schnittstellen|Kommentare|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Verwaltet den Buildvorgang einer Projektkonfiguration.|

### <a name="additional-project-objects"></a>Zusätzliche Projektobjekte

|Schnittstellen|Kommentare|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zeigt Elementeigenschaften im **Eigenschaftenfenster** an.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zeigt Ausgaben für die Bereitstellung an.|

 In der folgenden Tabelle finden Sie kurze Beschreibungen der im Projektmodell identifizierten Dienste.

### <a name="services"></a>Dienste

|Dienst|Kommentare|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Wird von VSPackages verwendet, die Projekttypen implementieren, um zu registrieren, dass ihre Projektfactory bei der IDE vorhanden ist. Ihr VSPackage `QueryService` muss diesen Dienst aufrufen und `IVsPackage::SetSite` seine Projektfactory registrieren, wenn die Methode aufgerufen wird. Wenn `SetSite` die Methode nicht aufgerufen wird, wird das Projekt nicht instanziiert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet Zugriff auf die interne, integrierte Vorstellung der ide der aktuellen Projektmappe, z. B. die Möglichkeit, Projekte aufzuzählen, neue Projekte zu erstellen, Projektänderungen zu beachten usw.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Aufruf von Projekten, die an der Quellcodeverwaltung teilnehmen möchten.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Verwaltet eine Tabelle mit geöffneten Dokumenten, um zu bestimmen, ob eines oder mehrere Projektelemente bereits geöffnet sind.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Enthält die Schnittstellen und Methoden, die aufgerufen werden, um ein Projektelement tatsächlich mit dem Standardeditor oder einem bestimmten Editor zu öffnen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Erforderlich, dass alle Projekte aufgerufen werden, wenn sie ihre Elemente hinzufügen, entfernen oder umbenennen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Verwaltet Änderungen an einer Datei oder einem Verzeichnis und benachrichtigt Clients, wenn ausgewählte Dateien auf dem Datenträger geändert wurden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Erforderlich, um von allen Projekten und Editoren aufgerufen werden, bevor sie schmutzige Elemente oder speichern sie.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Verwaltet die Reihenfolge der Build- und Bereitstellungsvorgänge für Projektkonfigurationen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Bietet Zugriff auf Low-Level-Debuggerdienste, die für die meisten Debugsteuerelemente verwendet werden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Ermöglicht VSPackages den Zugriff auf Informationen über aktuelle Auswahlen und ermöglicht die Kommunikation mit dem **Eigenschaftenfenster.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende UI-bezogene IDE-Funktionen, z. B. die Möglichkeit, Toolfenster oder Dokumentfenster zu erstellen und aufzuzählen oder dem Benutzer einen Fehler zu melden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Bietet Zugriff auf die Statusleiste der IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Wird verwendet, um das Automatisierungsmodell zu implementieren. In Ihrem Projektmodell geben Sie ein Eigenschaftenobjekt zurück, mit dem Sie eine Instanz dieses Objekts erstellen können.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Wird verwendet, um Zwischenablageereignisse für das Projektobjekt in der Hierarchie zu implementieren. `SVsUIHierWinClipboardHelper`können Sie Ausschneiden, Kopieren und Einfügen von Vorgängen korrekt behandeln.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
