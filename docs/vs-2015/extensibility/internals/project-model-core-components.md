---
title: Hauptkomponenten eines Projekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de65155e08f4c2410d19db1b25105d247c9f0952
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704115"
---
# <a name="project-model-core-components"></a>Hauptkomponenten eines Projektmodells
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In den folgenden Tabellen, die auf das Modell erweitert werden. Die Tabellen zeigen kurze Beschreibungen der Schnittstellen und -Dienste, die in das Modell und die Schnittstellen und Dienste im Zusammenhang mit der bestimmte Objekte identifiziert. Darüber hinaus Informationen in den Tabellen andere Schnittstellen, die in Project-Erstellung und Wartung je nach den Anforderungen Ihrer bestimmten Projekttyp optional sind.  
  
 Weitere Informationen finden Sie unter [Tools zum Durchsuchen von Symbolen unterstützen](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Paketobjekt  
  
|Interface|Kommentare|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Initialisiert ein VSPackage in der IDE, und macht seine Dienste für der IDE verfügbar.|  
  
### <a name="project-factory-object"></a>Projekt-Factory-Objekt  
  
|Interface|Kommentare|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Verwaltet Erstellen neuer Projekte und vorhandene Projekte öffnen.|  
  
### <a name="project-objects"></a>Project-Objekte  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Verwaltet das Hinzufügen und Entfernen von Projektelementen, Editoren geöffnet und verwaltet die Zuordnung zwischen einzelnen dokumentenmoniker und `VSITEMID`. Erbt von `IVsProject` und `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Verwaltet die Navigations-und anzeigen, und stellt Ereignisse bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Ermöglicht das befehlsausführung ähnelt der von `IOleCommandTarget` für Befehle wie Ausschneiden und umbenennen, die gelten nur, wenn der Fokus im Projektmappen-Explorer ist.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fungiert als die primäre befehlszielschnittstelle für einer Projekthierarchie. Es ist die Standardschnittstelle zum Abfragen von Objekten für ihren Befehlen der Status "oder" State "und" ausgeführt wird. Verfügbar, wenn Sie sich nicht im Projektfenster konzentrieren möchten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordiniert die Persistenz der Zustand des Projekts an. In der Regel der Projektzustand wird als eine Projektdatei gespeichert aber auf Speichersysteme, die nicht dateibasiert sind angepasst werden kann.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Können das Projekt aus, um alle Aspekte der Persistenz für deren Projektelemente, entweder als Dateien auf einem Datenträger oder Objekte in anderen Speichersystemen verwalten. Die `IVsPeristHierarchyItem2` Schnittstelle wird verwendet, für Elemente, die keine implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordiniert die Interaktionen mit quellcodeverwaltung.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Ermöglicht Projekten, Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Verwaltet die Konfiguration von Projektobjekten wie z. B. Debug/Release-Konfigurationen. Erstellen, bereitstellen und Debuggen Vorgänge werden über die Konfiguration von Projektobjekten koordiniert.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Durch Hierarchien, um das Löschen (destruktiver) zu steuern oder zu entfernen (nicht-destruktiver) Optionen für die Hierarchieelemente implementiert. Rufen Sie die Abfrageschnittstelle für den `IVsHierarchyDeleteHandler` -Schnittstelle aus der `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Bietet die implementierungsmöglichkeit, dass das Objekt, das unterstützt der `IVsCfgProvider2` Schnittstelle eine andere COM-Identität als das Projektobjekt, implementiert die `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Eine optionale Schnittstelle implementiert, um Ihr Projekt extensible von anderen Entwicklern. Die `IVsProjectStartupServices` Schnittstelle ermöglicht ein VSPackage von Drittanbietern, um eine GUID zu registrieren, die Sie in der Projektdatei beibehalten werden, damit jedes Mal, wenn das Projekt geladen wird, die von Drittanbietern-GUID in Ihrer Projektdatei, und rufen laden `QueryService` für diese GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Quellhierarchien in implementiert eine `UIHierarchy` Fenster koordiniert Zwischenablageoperationen wie z. B. Ausschneide-, Kopier-und einfügen. Verwenden der `AdviseClipboardHelperEvents` Schnittstelle Zwischenablage Ereignisse registrieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Enthält Informationen über ein gezogenes Element relativ zu seiner Datenquelle während eines Drag & Drop-Vorgangs im Benutzeroberflächen-hierarchienfensters. Wird aufgerufen, von der `IVsHierarchy` Schnittstelle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Enthält Informationen über ein gezogenes Element relativ zu dessen Ablageziel während eines Drag & Drop-Vorgangs im Benutzeroberflächen-hierarchienfensters. Wird aufgerufen, von der `IVsHierarchy` Schnittstelle.|  
  
### <a name="configuration-object"></a>Configuration-Objekt  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Enthält Informationen zu einer Konfiguration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Ermöglicht Projekten, Konfigurationsinformationen zu verwalten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Ermöglicht einem Projekt unter der Kontrolle des Debuggers ausgeführt werden muss.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementiert durch die Bereitstellung von Projekten, die Bereitstellungsvorgänge für andere Projekte ausführen.|  
  
### <a name="configuration-builder-object"></a>Konfigurations-Generator-Objekt  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Verwaltet die Buildvorgang einer Projektkonfiguration.|  
  
### <a name="additional-project-objects"></a>Zusätzliche Projektobjekten  
  
|Schnittstellen|Kommentare|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zeigt die Elementeigenschaften in den **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zeigt die Ausgaben für die Bereitstellung an.|  
  
 Die folgende Tabelle enthält kurze Beschreibungen der Dienste, die in das Modell identifiziert.  
  
### <a name="services"></a>Dienste  
  
|Dienst|Kommentare|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Wird von VSPackages verwendet, die Projekttypen registrieren zu implementieren, dass die Projekt-Factory mit der IDE vorhanden ist. Muss Ihr VSPackage Aufrufen `QueryService` für diesen Dienst, und Registrieren der Projektzuordnungsinstanz bei `IVsPackage::SetSite` Methode wird aufgerufen. Wenn die `SetSite` -Methode nicht aufgerufen wird, das Projekt kann nicht instanziiert werden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet Zugriff auf die IDE internen, integrierte Konzept der aktuellen Projektmappe ein, z.B. die Möglichkeit, Projekte auflisten, neue Projekte erstellen, beachten Sie projektänderungen und so weiter.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wird von Projekten aufgerufen, die in der quellcodeverwaltung teilnehmen möchten.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Verwaltet eine Tabelle der geöffneten Dokumente zu bestimmen, ob eine oder mehrere der Ihrer Projektelemente sind bereits geöffnet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Enthält Schnittstellen und Methoden aufgerufen, um tatsächlich ein Projektelement mit der standard-Editor oder einen bestimmten Editor zu öffnen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Erforderlich, um alle Projekte aufgerufen werden, wenn sie hinzufügen, entfernen oder benennen Sie ihre Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Änderungen an einer Datei oder Verzeichnis verwaltet, und Clients darüber benachrichtigt, wenn ausgewählte Dateien auf dem Datenträger geändert wurden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Erforderlich, um alle Projekte und Editoren aufgerufen werden, bevor sie Elemente geändert, oder speichern Sie sie.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Verwaltet die Reihenfolge der Build & Deployment-Vorgänge für Projektkonfigurationen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Bietet Zugriff auf Low-Level-Debugger-Dienste, die für die meisten Debuggen Steuerelemente verwendet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Ermöglicht VSPackages den Zugriff auf Informationen über die aktuelle Auswahl und ermöglicht die Kommunikation mit dem **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende Benutzeroberflächenelement IDE-Funktionen, z. B. die Möglichkeit zum Erstellen und Auflisten von Toolfenster oder Dokumentfenster oder einen Fehler für den Benutzer zu melden.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Bietet Zugriff auf die IDE Statusleiste angezeigt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Zum Implementieren des Automatisierungsmodells verwendet. In Ihrem Projektmodell dem, wird nun wieder eine Properties-Objekt, mit dem Sie erstellt eine Instanz dieses Objekts.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Verwendet, um die Ereignisse der Zwischenablage auf das Projektobjekt, in der Hierarchie zu implementieren. `SVsUIHierWinClipboardHelper` Sie können ordnungsgemäß Handle Ausschneiden, kopieren und einfügen.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nicht im Build: Mithilfe von HierUtil7 Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Unterstützung von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
