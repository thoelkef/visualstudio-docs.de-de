---
title: Verwandte Dienste und Schnittstellen (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e68c7c0101661ae9afffa7e9e12e8e4faa44fc7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940488"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Verwandte Dienste und Schnittstellen (Quellcodeverwaltungs-VSPackage)
Dieser Abschnitt enthält alle VSPackage sammlungsbezogene Schnittstellen in der Quellcode der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Das Quellcodeverwaltungs-VSPackage implementiert einige dieser Schnittstellen und andere um Aufgaben der quellcodeverwaltung zu erreichen.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Schnittstellen implementiert und für Quellcodeverwaltungs-VSPackages  
 Die folgenden Schnittstellen werden beschrieben, der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], und das Quellcodeverwaltungs-VSPackage implementiert eine Teilmenge davon abhängig von der gewünschten Funktionsumfang. Einige Schnittstellen sind gekennzeichnet. als erforderlich und muss mit jeder Datenquellen-Steuerelement VSPackage implementiert werden.  
  
 Zu diesen Schnittstellen, die ein Paket nicht implementiert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt eine Standardimplementierung bereit. Beachten Sie, dass die standardmäßige Implementierung für den Fall konzipiert ist, wenn keine VSPackage registriert ist und kein Projekt gesteuert wird. Ein ordentlich geschriebenen Quellcodeverwaltungs-VSPackage implementiert alle erforderlichen Schnittstellen anstatt über überlassen sie die standardmäßige Implementierung dieser Schnittstellen.  
  
 Ein Quellcodeverwaltungs-VSPackage muss einen privaten Dienst implementieren, der einige oder alle der folgenden Schnittstellen kapselt.  
  
 Schnittstellen sind:  
  
-   Erforderlich: Die entsprechende Entität (Datenquellen-Steuerelement VSPackage, Quellcode-Verwaltungsstub Projekt) muss die Schnittstelle implementieren.  
  
-   Empfohlen: Die Entität sollten diese Schnittstelle implementieren; Andernfalls kann Quellcodeverwaltungsfunktionen beschränkt sein.  
  
-   Optional: die Entität kann diese Schnittstelle, um einen größeren Funktionsumfang bieten implementieren.  
  
| Interface | Zweck | Implementiert von | Implementiert werden? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editoren rufen Sie diese Schnittstelle vor dem ändern oder Speichern einer Datei. Das Datenquellen-Steuerelement VSPackage kann die Datei auschecken oder verweigern den Vorgang aus, wenn das Auschecken fehlschlägt. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Diese Schnittstelle bietet grundlegende Quellcodeverwaltungsfunktionen für Projekte, wie z. B. registrieren und Aufheben der Registrierung für Projekte mit quellcodeverwaltung und bieten Unterstützung für grundlegende Quellcodeverwaltungssymbole an. | Datenquellen-Steuerelement VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Diese Schnittstelle wird abrufen, aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mithilfe der <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> -Funktion, oder wandeln einfach die objektimplementierung `IVsHierarchy` zu `IVsSccProject2`. Es dient zum Abrufen von Dateien unter quellcodeverwaltung in einem Projekt oder für das Projekt mit den aktuellen Status der quellcodeverwaltung oder den Speicherort zu informieren. | Projekt | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Das Integrationsmodul verwendet diese Schnittstelle, um das aktuelle aktive VSPackage festzulegen. | Datenquellen-Steuerelement VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Diese Schnittstelle basiert auf ein Abonnementmodell. Jedem VSPackage kann darauf hinweisen, dass der Dokumentereignisse empfangen und von der Shell empfohlen werden, die auf Ereignissen, die sind im Begriff, die auftreten, möchte. Es implementiert und von behandelt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], der wiederum übergibt Ereignisse implementieren die `IVsTrackProjectDocumentsEvents2` für das VSPackage. | Quellcode-Verwaltungsstub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Diese Schnittstelle bietet, Batchverarbeitung, synchronisierte Lese-/Schreibvorgänge und eine erweiterte `OnQueryAddFiles` Methode. | Quellcode-Verwaltungsstub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Projektmappen-Explorer** und Projekte dieser Schnittstelle aufrufen, wenn neue Dateien an den Projekten hinzugefügt werden, oder wenn Dateien und Ordner umbenannt oder aus Projekten gelöscht werden. Das Quellcodeverwaltungs-VSPackage kann sehen Sie sich die Projektdatei, oder brechen Sie den Vorgang. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Projektmappen-Explorer** , und rufen Sie diese Schnittstelle als Reaktion auf Aufrufe der Methoden der Schnittstelle IVstrackProjectDocuments3 Projekte. Das Datenquellen-Steuerelement, das VSPackage kann Batch-Vorgänge, synchronisiert nachverfolgen Lese-/Schreibvorgänge und Arbeiten mit einer erweiterten `OnQueryAddFiles` Methode. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Diese Schnittstelle bietet Eintragung Verwaltungssupport für Webprojekte. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Diese Schnittstelle wird verwendet, um QuickInfos für die der quellcodeverwaltung unterliegende Dateien in den Projekten abzurufen. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Diese Schnittstelle bietet Unterstützung für Namespace-Erweiterung. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Das VSPackage verwendet diese Schnittstelle zum Integrieren einer Erweiterungs des Namespaces in der **neu**, **öffnen**, oder **speichern** Dialogfelder. Folglich Projekte automatisch quellcodeverwaltung bei der Erstellung hinzugefügt, oder hinzugefügt werden können, quellcodeverwaltung, sobald ein Speichervorgang-Vorgang ist aktiv. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Das VSPackage verwendet diese Schnittstelle, um zusätzliche Symbole als Quellcodeverwaltungssymbole für Knoten in definieren **Projektmappen-Explorer**. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Die **hinzufügen** für Webprojekte im Dialogfeld verwendet diese Schnittstelle. Es bietet Methoden zum Durchsuchen für einen Speicherort auf dem Quellcode und für das Öffnen eines Webprojekts, das zuvor in das Quellcodeverwaltungs-Repository an dieser Stelle hinzugefügt. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Diese Schnittstelle bietet Unterstützung für asynchrone (Hintergrund) beim Laden von Projekten aus der quellcodeverwaltung. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Diese Schnittstelle ermöglicht es, Projekte überwacht den Status des asynchronen Laden von initiiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Projekt | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Diese Schnittstelle ermöglicht es, die IDE das aktive Quellcodeverwaltungs-VSPackage abgefragt wird. Die IDE fragt den Wert des Quellcode-verwaltungseinstellungen, die Bedeutung haben, auch wenn keine aktiven Datenquellen-Steuerelement, die VSPackage registriert. Diese Schnittstelle implementiert wird, und behandelt, indem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Quellcode-Verwaltungsstub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Diese Schnittstelle wird verwendet, bei der Registrierung des Quellcodeverwaltungs-VSPackage. | Quellcode-Verwaltungsstub | Erforderlich |
| <xref:EnvDTE.SourceControl> | Diese Schnittstelle wird in Automation verwendet. Daher macht es nur Funktionen, die ausgeführt werden können, ohne dass Sie keine Benutzeroberfläche angezeigt. | Datenquellen-Steuerelement VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Diese Schnittstelle wird verwendet, um die Quelle in der Projektmappendatei (.sln) Einstellungen zu speichern. Die Einstellungen umfassen den Speicherort auf dem Quellcode und die Statusflags für Quelle-Steuerelement. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Diese Schnittstelle wird verwendet, um die Einstellungen der quellcodeverwaltung in der Projektmappendatei (SUO)-Optionen zu speichern. Dies kann es sich um benutzerspezifische Quellcode-verwaltungseinstellungen, z. B. die aktuelle Position des Benutzers Eintragung umfassen. | Datenquellen-Steuerelement VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Diese Schnittstelle wird zum Überwachen von Ereignissen verwendet, damit Sie Vorgänge wie z. B. das Einchecken von Dateien des Projekts vor dem Schließen von Projektmappen oder neue Dateien aus der quellcodeverwaltung abrufen, beim Öffnen eines Projekts ausführen. | Datenquellen-Steuerelement VSPackage | Empfohlen |
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)