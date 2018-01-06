---
title: Modell-Kernkomponenten Projekt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d2de7b73238589786c1e8a4ba42389201123c2b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="project-model-core-components"></a>Projekt-Modell-Kernkomponenten
In den folgenden Tabellen, die auf das Projektmodell erweitert werden. In den Tabellen vorhanden, kurze Beschreibung der Schnittstellen und Dienste, die in das Modell und die Schnittstellen und Dienste, mit spezifischen Objekten verknüpft sind. Darüber hinaus enthalten die Tabellen Details anderer Schnittstellen, die im projekterstellung und Wartung je nach den Anforderungen Ihrer bestimmten Projekttyp optional sind.  
  
 Weitere Informationen finden Sie unter [Tools zum Durchsuchen des Symbols unterstützen](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Paketobjekt  
  
|Interface|Kommentare|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialisiert eine VSPackage in der IDE und stellt seine Dienste der IDE zur Verfügung.|  
  
### <a name="project-factory-object"></a>Projekt-Factoryobjekt  
  
|Interface|Kommentare|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Verwaltet die neue Projekte erstellen und vorhandene Projekte öffnen.|  
  
### <a name="project-objects"></a>Projektobjekte  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Das Hinzufügen und Entfernen von Projektelementen verwaltet, öffnet Editoren und verwaltet die Zuordnung zwischen den einzelnen dokumentmoniker und die `VSITEMID`. Erbt von `IVsProject` und `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Verwaltet Navigations- und Anzeige von Eigenschaften und Ereignisse enthält.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Ermöglicht das befehlsausführung ähnlich dem Konzept `IOleCommandTarget` für Befehle wie z. B. Ausschneide- und umbenennen, die gelten nur, wenn der Fokus im Projektmappen-Explorer ist.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fungiert als die primäre befehlszielschnittstelle für eine Projekthierarchie. Es ist die standard-Schnittstelle zum Abfragen von Objekten für ihre Befehle der Status "oder" State "und" ausgeführt wird. Verfügbar, wenn Sie nicht im Projektfenster Fokus befindet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordiniert die Persistenz des Projektzustands an. In der Regel des Projektzustands ist als eine Projektdatei gespeichert aber auf Speichersysteme, die nicht dateibasiert sind angepasst werden kann.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Ermöglicht es das Projekt alle Aspekte der Persistenz für deren Projektelemente, entweder als Dateien auf einem Datenträger oder Objekte in anderen Speichersystemen verwaltet. Die `IVsPeristHierarchyItem2` Schnittstelle wird verwendet, für Elemente, die keine implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordiniert Interaktionen mit der quellcodeverwaltung an.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Teammodells werden Projekte, um Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Projekt-Konfigurationsobjekte, z. B. Debug/Releasekonfigurationen wird verwaltet. Erstellen, bereitstellen und Debuggen Vorgänge werden über den Projekt-Konfigurationsobjekte koordiniert.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Durch Hierarchien zu löschen (destruktiver) zu steuern oder zu entfernen (nicht destruktiver) Optionen für die Hierarchieelemente implementiert. Rufen Sie die Abfrageschnittstelle für die `IVsHierarchyDeleteHandler` -Schnittstelle aus der `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Bietet die Möglichkeit, dass das Objekt, das unterstützt Implementierung der `IVsCfgProvider2` Schnittstelle auf einer anderen COM-Identität als das Projektobjekt, die implementiert die `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Eine optionale Schnittstelle implementiert, um das Projekt erweiterbar gemacht von anderen Entwicklern. Die `IVsProjectStartupServices` Schnittstelle ermöglicht eine VSPackage eines Drittanbieters, um eine GUID zu registrieren, die Sie in der Projektdatei beibehalten werden, damit jedes Mal, wenn das Projekt geladen wird, die Drittanbieter-Dienst-GUID in der Projektdatei, und rufen laden `QueryService` für diese GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementiert durch Quellhierarchien in einem `UIHierarchy` Fenster koordinieren Zwischenablagevorgänge wie Ausschneiden, kopieren und einfügen. Verwenden der `AdviseClipboardHelperEvents` Schnittstelle Zwischenablage Ereignisse registrieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Enthält Informationen über ein gezogenes Element relativ zu dessen Datenquelle während eines Drag & Drop-Vorgangs in einem UI-Fenster "Aufrufhierarchie". Wird aufgerufen, aus der `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Enthält Informationen über ein gezogenes Element relativ zu dessen Ablageziel während eines Drag & Drop-Vorgangs in einem UI-Fenster "Aufrufhierarchie". Wird aufgerufen, aus der `IVsHierarchy` Schnittstelle.|  
  
### <a name="configuration-object"></a>Configuration-Objekt  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Enthält Informationen zu einer Konfiguration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Teammodells werden Projekte, um Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Kann ein Projekt unter der Kontrolle des Debuggers ausgeführt werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementiert durch Bereitstellungsprojekte, die Bereitstellungsvorgänge für andere Projekte ausführen.|  
  
### <a name="configuration-builder-object"></a>Configuration-Generator-Objekt  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Verwaltet eine Projektkonfiguration Erstellungsvorgang.|  
  
### <a name="additional-project-objects"></a>Zusätzliche Project-Objekte  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zeigt die Elementeigenschaften in den **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zeigt die Ausgaben für die Bereitstellung an.|  
  
 Die folgende Tabelle enthält kurze Beschreibungen der Dienste, die in das Modell identifiziert.  
  
### <a name="services"></a>Dienste  
  
|Dienst|Kommentare|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Verwendet von VSPackages, die Projekttypen registrieren zu implementieren, dass ihre Project-Factory mit der IDE vorhanden ist. Ihr VSPackage muss Aufrufen `QueryService` für diesen Dienst, und registrieren Sie die Project-Factory beim `IVsPackage::SetSite` Methode wird aufgerufen. Wenn die `SetSite` -Methode nicht aufgerufen wird, das Projekt kann nicht instanziiert werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet Zugriff auf die IDE internen, integrierte Konzept der aktuellen Projektmappe befinden, z. B. das Aufzählen von Projekten, neue Projekte erstellen, berücksichtigen, projektänderungen usw.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wird aufgerufen, Projekte, die in der quellcodeverwaltung teilnehmen möchten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Verwaltet eine Tabelle der geöffneten Dokumente zu bestimmen, ob eine oder mehrere der Projektelemente bereits geöffnet sind.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Enthält die Schnittstellen und Methoden, die aufgerufen wird, um tatsächlich ein Projektelement mit standard-Editor oder einen bestimmten Editor zu öffnen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Erforderlich, um alle Projekte aufgerufen werden, wenn sie hinzufügen, entfernen oder benennen Sie ihre Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Änderungen an einer Datei oder Verzeichnis verwaltet und benachrichtigt Clients aus, wenn die ausgewählte Dateien auf dem Datenträger geändert wurden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Erforderlich, um alle Projekte und Editoren aufgerufen werden, bevor sie Elemente modifizierte oder speichern Sie sie.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Verwaltet die Reihenfolge der Build- und Bereitstellungsprozess Vorgänge für Projektkonfigurationen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Bietet Zugriff auf Low-Level-Debugger-Dienste, die für die meisten debugging-Steuerelemente verwendet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Ermöglicht VSPackages den Zugriff auf Informationen zur aktuellen Auswahl und ermöglicht die Kommunikation mit dem **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Stellt grundlegende Benutzeroberfläche bezogenen IDE-Funktionen, z. B. die Fähigkeit zum Erstellen und Auflisten von Toolfenster oder Dokumentfenster oder um einen Fehlerbericht an den Benutzer bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Bietet Zugriff auf die IDE-Statusleiste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Wird verwendet, um das Automatisierungsmodell implementieren. In Ihrem Projektmodell wird nun wieder ein Objekt für Eigenschaften, mit dem Sie erstellt eine Instanz dieses Objekts.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Verwendet, um der Zwischenablage Ereignisse auf das Objekt in der Hierarchie implementieren. `SVsUIHierWinClipboardHelper`Sie können ordnungsgemäß Handle Ausschneiden, kopieren und einfügen.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nicht im Build: Verwenden von HierUtil7 Projektklassen zum Implementieren von eines Projekttyps (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)