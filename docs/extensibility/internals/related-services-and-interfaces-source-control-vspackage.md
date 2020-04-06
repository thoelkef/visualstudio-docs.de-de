---
title: Verwandte Dienste und Schnittstellen (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705627"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Verwandte Dienste und Schnittstellen (Quellcodeverwaltungs-VSPackage)
In diesem Abschnitt werden alle Quellcodeverwaltungsschnittstellen im [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]VSPackage-bezogenen Schnittstellen aufgelistet. Die Quellcodeverwaltung VSPackage implementiert einige dieser Schnittstellen und verwendet andere, um Quellcodeverwaltungsaufgaben auszuführen.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Schnittstellen Implementiert von und für Source Control VSPackages
 Die folgenden Schnittstellen werden [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]im beschrieben, und die Quellcodeverwaltung VSPackage implementiert je nach gewünschtem Feature-Set eine Teilmenge davon. Einige Schnittstellen sind als erforderlich gekennzeichnet und müssen von jedem Quellcodeverwaltungs-VSPackage implementiert werden.

 Für Schnittstellen, die von einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paket nicht implementiert werden, wird eine Standardimplementierung angegeben. Beachten Sie, dass die Standardimplementierung für den Fall konzipiert ist, dass kein VSPackage registriert ist und kein Projekt gesteuert wird. Ein ordnungsgemäß geschriebenes Quellcodeverwaltungssteuerelement VSPackage implementiert alle erforderlichen Schnittstellen, anstatt es der Standardimplementierung dieser Schnittstellen zu überlassen.

 Ein Quellcodeverwaltungs-VSPackage muss einen privaten Dienst implementieren, der einige oder alle der folgenden Schnittstellen kapselt.

 Schnittstellen sind:

- Erforderlich: Die entsprechende Entität (Quellcodeverwaltung VSPackage, Source Control Stub, Project) muss die Schnittstelle implementieren.

- Empfohlen: Die Entität sollte diese Schnittstelle implementieren. Andernfalls kann die Quellcodeverwaltungsfunktionalität eingeschränkt sein.

- Optional: Die Entität kann diese Schnittstelle implementieren, um einen umfassenderen Featuresatz bereitzustellen.

| Schnittstelle | Zweck | Implementiert von | Implementieren? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editoren rufen diese Schnittstelle auf, bevor Sie eine Datei ändern oder speichern. Die Quellcodeverwaltung VSPackage kann die Datei auschecken oder den Vorgang verweigern, wenn das Auschecken fehlschlägt. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Diese Schnittstelle bietet grundlegende Quellcodeverwaltungsfunktionen für Projekte, z. B. das Registrieren und Aufheben der Registrierung von Projekten bei der Quellcodeverwaltung und die Unterstützung grundlegender Quellcodeverwaltungs-Glyphen. | Quellcodeverwaltung VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Diese Schnittstelle wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> aus <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> der Verwendung der Funktion oder `IVsHierarchy` `IVsSccProject2`durch einfaches Umwerfen des Objekts, das implementiert wird, auf erhalten. Es wird verwendet, um die Dateien in einem Projekt unter Quellcodeverwaltung zu stellen oder um das Projekt über den aktuellen Quellcodeverwaltungsstatus oder Speicherort zu informieren. | Project | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Das Integrationsmodul verwendet diese Schnittstelle, um das aktuelle aktive VSPackage festzulegen. | Quellcodeverwaltung VSPackage | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Diese Schnittstelle basiert auf einem Abonnementmodell. Jedes VSPackage kann signalisieren, dass es Dokumentereignisse empfangen möchte, und von der Shell über Ereignisse informiert werden, die im Begriff sind. Sie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert und behandelt, die `IVsTrackProjectDocumentsEvents2` wiederum Ereignisse übergibt, die die an das VSPackage implementieren. | Quellsteuerungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Diese Schnittstelle bietet Batchverarbeitung, synchronisierte Lese-/Schreibvorgänge und eine erweiterte `OnQueryAddFiles` Methode. | Quellsteuerungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Projektmappen-Explorer** und Projekte rufen diese Schnittstelle auf, wenn den Projekten neue Dateien hinzugefügt werden oder wenn Dateien und Ordner umbenannt oder aus Projekten gelöscht werden. Die Quellcodeverwaltung VSPackage kann die Projektdatei auschecken oder den Vorgang abbrechen. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Projektmappen-Explorer** und Projekte rufen diese Schnittstelle als Reaktion auf Aufrufe an die Methoden der IVstrackProjectDocuments3-Schnittstelle auf. Das Quellcodeverwaltungs-VSPackage kann Batchvorgänge, synchronisierte Lese-/Schreibvorgänge und `OnQueryAddFiles` arbeiten mit einer erweiterten Methode nachverfolgen. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Diese Schnittstelle bietet Unterstützung für das Inlistment-Management für Webprojekte. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Diese Schnittstelle wird verwendet, um ToolTips für die Quelldateien in den Projekten abzurufen. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Diese Schnittstelle bietet Unterstützung für Namespaceerweiterungen. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Das VSPackage verwendet diese Schnittstelle, um eine Namespaceerweiterung in die Dialogfelder **Neu,** **Öffnen**oder **Speichern** zu integrieren. Folglich können Projekte bei der Erstellung automatisch zur Quellcodeverwaltung oder zur Quellcodeverwaltung hinzugefügt werden, wenn ein Speichervorgang aktiviert ist. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Das VSPackage verwendet diese Schnittstelle, um zusätzliche Glyphen als Quellcodeverwaltungsglyphen für Knoten im **Projektmappen-Explorer**zu definieren. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Das Dialogfeld **Hinzufügen** für Webprojekte verwendet diese Schnittstelle. Es bietet Methoden zum Durchsuchen eines Quellcodeverwaltungsspeicherorts und zum Öffnen eines Webprojekts, das zuvor im Quellcodeverwaltungsrepository an diesem Speicherort hinzugefügt wurde. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Diese Schnittstelle bietet Unterstützung für das asynchrone (Hintergrund-)Laden von Projekten aus der Quellcodeverwaltung. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Diese Schnittstelle ermöglicht es Projekten, den Fortschritt <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>des asynchronen Ladens zu beobachten, das von initiiert wird. | Project | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Diese Schnittstelle ermöglicht es der IDE, die aktive Quellcodeverwaltung VSPackage abzufragen. Die IDE fragt den Wert der Quellcodeverwaltungseinstellungen ab, die auch dann Bedeutung haben, wenn kein aktives Quellcodeverwaltungs-VSPackage registriert ist. Diese Schnittstelle wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert und verarbeitet. | Quellsteuerungs-Stub | Erforderlich |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Diese Schnittstelle wird bei der Registrierung der Quellcodeverwaltung VSPackage verwendet. | Quellsteuerungs-Stub | Erforderlich |
| <xref:EnvDTE.SourceControl> | Diese Schnittstelle wird in der Automatisierung verwendet. Daher werden nur Funktionen verfügbar gemacht, die ausgeführt werden können, ohne dass eine Benutzeroberfläche angezeigt wird. | Quellcodeverwaltung VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Diese Schnittstelle wird verwendet, um die Quellcodeverwaltungseinstellungen in der Projektmappe (.sln) zu speichern. Die Einstellungen umfassen die Quellsteuerungsposition und die Statusflags der Quellcodeverwaltung. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Diese Schnittstelle wird verwendet, um die Quellcodeverwaltungseinstellungen in der Projektmappenoptionendatei (.suo) zu speichern. Dies kann benutzerspezifische Quellcodeverwaltungseinstellungen wie den Anmeldespeicherort des aktuellen Benutzers umfassen. | Quellcodeverwaltung VSPackage | Empfohlen |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Diese Schnittstelle wird verwendet, um Ereignisse zu überwachen, um Vorgänge wie das Einchecken von Projektdateien vor dem Schließen von Projektlösungen oder das Abrufen neuer Dateien aus der Quellcodeverwaltung beim Öffnen eines Projekts auszuführen. | Quellcodeverwaltung VSPackage | Empfohlen |

## <a name="see-also"></a>Weitere Informationen
- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
