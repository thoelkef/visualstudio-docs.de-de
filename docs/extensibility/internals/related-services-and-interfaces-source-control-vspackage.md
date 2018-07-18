---
title: Verknüpfte Dienste und Schnittstellen (Source Control VSPackage) | Microsoft Docs
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
ms.openlocfilehash: 1f9e8e90fdda61524a9af107df452bc2b13cd90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135351"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Verknüpfte Dienste und Schnittstellen (Source Control VSPackage)
Dieser Abschnitt enthält alle in der Quelle zu steuern, VSPackage-Schnittstellen in den [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Die Datenquellen-Steuerelements VSPackage implementiert einige dieser Schnittstellen und andere um Quellcodeverwaltungsaufgaben zu erreichen.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Schnittstellen implementiert und für Datenquellen-Steuerelement VSPackages  
 Die folgenden Schnittstellen in beschriebenen der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], und das Quellsteuerelement VSPackage implementiert eine Teilmenge davon abhängig von der entsprechenden Featuregruppe gewünschten. Einige Schnittstellen werden markiert. wie erforderlich und muss von jedem quellcodeverwaltung VSPackage implementiert werden.  
  
 Zu diesen Schnittstellen, die ein Paket nicht implementiert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt eine Standardimplementierung bereit. Beachten Sie, dass die standardmäßige Implementierung für die Groß-/Kleinschreibung ausgelegt ist, wenn keine VSPackage registriert ist, und es wird kein Projekt gesteuert. Ein ordnungsgemäß geschrieben Quellcodeverwaltungs VSPackage implementiert alle notwendigen Schnittstellen, anstatt sie die standardmäßige Implementierung dieser Schnittstellen überlassen.  
  
 Ein VSPackage des Datenquellen-Steuerelement muss einen privaten Dienst implementieren, der einige oder alle der folgenden Schnittstellen kapselt.  
  
 Schnittstellen sind:  
  
-   Erforderlich: Die entsprechende Entität (Datenquellen-Steuerelements VSPackage, Datenquellen-Steuerelement-Stub-Projekt) muss die Schnittstelle implementieren.  
  
-   Empfohlen: Die Entität sollten diese Schnittstelle implementieren. andernfalls möglicherweise Quellcodeverwaltungsfunktion beschränkt sind.  
  
-   Optional: die Entität kann diese Schnittstelle, um einen größeren Funktionsumfang bieten implementieren.  
  
|Interface|Zweck|Implementiert durch|Implementieren?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editoren rufen Sie diese Schnittstelle vor dem ändern oder eine Datei speichern. Die Datenquellen-Steuerelements VSPackage kann die Datei auschecken oder verweigern den Vorgang aus, schlägt das Auschecken rückgängig.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Diese Schnittstelle bietet grundlegende Quellcodeverwaltungsfunktion für Projekte, wie z. B. registrieren und Aufheben der Registrierung für Projekte mit der quellcodeverwaltung und Bereitstellen von Unterstützung für grundlegende Source Control Symbole.|Datenquellen-Steuerelements VSPackage|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Diese Schnittstelle wird abgerufen, von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mithilfe der <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> -Funktion oder durch Umwandlung einfach auf das Objekt, durch `IVsHierarchy` auf `IVsSccProject2`. Es dient zum Abrufen von Dateien unter quellcodeverwaltung in einem Projekt oder für das Projekt aus, der den aktuellen Status des Quell- oder den Speicherort zu informieren.|Projekt|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Das Integrationsmodul verwendet diese Schnittstelle, um die aktuelle aktive VSPackage festzulegen.|Datenquellen-Steuerelements VSPackage|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Diese Schnittstelle basiert auf einem Abonnementmodell. Alle VSPackage kann darauf hinweisen, dass eine Verbindung Dokumentereignisse erhalten und werden von der Shell auf Ereignisse, die geprüft werden sollten. Es implementiert und von behandelt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], wiederum übergibt die Ereignisse, die Implementierung der `IVsTrackProjectDocumentsEvents2` für das VSPackage.|Source Control Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Diese Schnittstelle bietet, Batchverarbeitung, synchronisierte Lese-/Schreibvorgänge und eine erweiterte `OnQueryAddFiles` Methode.|Source Control Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Projektmappen-Explorer** und Projekte rufen diese Schnittstelle, wenn die Projekte neue Dateien hinzugefügt werden, oder Dateien und Ordner umbenannt oder gelöscht, die aus Projekten. Das Quellsteuerelement VSPackage kann sehen Sie sich die Projektdatei, oder brechen Sie den Vorgang.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Projektmappen-Explorer** , und rufen Sie diese Schnittstelle als Antwort auf die Aufrufe an die Methoden der Schnittstelle IVstrackProjectDocuments3 Projekte. Die Datenquellen-Steuerelements, das VSPackage Batch-Vorgänge synchronisiert verfolgen kann Vorgänge Lese-/Schreibzugriff und Arbeiten mit einer komplexeren `OnQueryAddFiles` Methode.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Diese Schnittstelle bietet Eintragung Management für Webprojekte zu unterstützen.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Diese Schnittstelle wird zum Abrufen von QuickInfos für die quellcodeverwaltete Dateien in Projekten verwendet.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Diese Schnittstelle bietet Unterstützung für die Erweiterung von Namespaces.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|Das VSPackage verwendet diese Schnittstelle zum Integrieren einer Namespace-Erweiterungs in der **neu**, **öffnen**, oder **speichern** Dialogfelder. Folglich Projekte automatisch auf die Erstellung von Datenquellen-Steuerelement hinzugefügt, oder hinzugefügt werden können zur quellcodeverwaltung, sobald ein Speichervorgang Vorgang gültig ist.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|Das VSPackage verwendet diese Schnittstelle so definieren Sie zusätzliche Symbole als Quelle Steuerelement Symbole für Knoten im **Projektmappen-Explorer**.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Die **hinzufügen** Dialogfeld für Webprojekte verwendet diese Schnittstelle. Es bietet Methoden zum Durchsuchen für ein Steuerelement Quellspeicherort und Öffnen eines Webprojekts, die zuvor in den Quellcodeverwaltungs-Repository an dieser Stelle hinzugefügt.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Diese Schnittstelle bietet Unterstützung für asynchrone (im Hintergrund) beim Laden von Projekten aus der quellcodeverwaltung an.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Diese Schnittstelle ermöglicht es, Projekte überwacht den Status des asynchronen Ladevorgangs gestartet, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Projekt|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Diese Schnittstelle ermöglicht es die IDE zum Abfragen der aktiven quellcodeverwaltung VSPackage. Die IDE fragt den Wert der quellcodeverwaltungseinstellungen, die Bedeutung haben, auch wenn keine aktiven Quellcodeverwaltungsprogramm VSPackage registriert ist. Diese Schnittstelle implementiert und von behandelt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Source Control Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Diese Schnittstelle wird verwendet, in die quellcodeverwaltung VSPackage registrieren.|Source Control Stub|Erforderlich|  
|<xref:EnvDTE.SourceControl>|Diese Schnittstelle wird bei der Automatisierung verwendet. Daher macht es nur Funktionen, die ohne Anzeige einer Benutzeroberfläche ausgeführt werden können.|Datenquellen-Steuerelements VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Diese Schnittstelle wird verwendet, um die Quelle Steuerung von Einstellungen in der Projektmappendatei (sln) speichern. Die Einstellungen enthalten die Quellspeicherort-Steuerelement und die Statusflags für Datenquellen-Steuerelement.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Diese Schnittstelle wird verwendet, um die Einstellungen für quellcodeverwaltung in der Projektmappendatei-Optionen (.suo) zu speichern. Dies kann benutzerspezifische Einstellungen für quellcodeverwaltung wie der aktuelle Benutzer Eintragung Speicherort umfassen.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Diese Schnittstelle wird zum Überwachen von Ereignissen verwendet, um Vorgänge ausführen wie das Einchecken von Projektdateien vor dem Schließen von Projektmappen oder neue Dateien aus der quellcodeverwaltung abrufen, wenn Sie ein Projekt zu öffnen.|Datenquellen-Steuerelements VSPackage|Empfohlen|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)