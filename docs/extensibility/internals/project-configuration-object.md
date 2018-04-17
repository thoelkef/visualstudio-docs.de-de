---
title: Konfigurationsobjekt Projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-object"></a>Projekt-Konfigurationsobjekt
Das Konfigurationsobjekt Projekt verwaltet die Anzeige der Konfigurationsinformationen auf der Benutzeroberfläche.  
  
 ![Visual Studio-Projektkonfiguration](../../extensibility/internals/media/vsprojectcfg.gif "VsProjectCfg")  
Eigenschaftenseiten für Projekt-Konfiguration  
  
 Der Konfigurationsanbieter Projekt verwaltet die Projektkonfigurationen. Die Umgebung und anderen Paketen, Zugriff auf und Abrufen von Informationen zu Konfigurationen eines Projekts, das Projekt Konfigurationsanbieter Objekt zugeordneten Schnittstellen aufzurufen.  
  
> [!NOTE]
>  Sie können nicht erstellen oder bearbeiten die Konfigurationsdateien für die Lösung programmgesteuert. Verwenden Sie `DTE.SolutionBuilder`. Finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md) für Weitere Informationen.  
  
 Um einen Anzeigenamen ein, in der Konfigurations-UI verwendet werden zu veröffentlichen, sollten das Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, womit eine Liste der `IVsCfg` Zeiger, die Sie verwenden können, zum Abrufen von Anzeigenamen für die Konfiguration und Plattform Informationen in der Umgebung Benutzeroberfläche aufgelistet werden. Die aktive Konfiguration und Plattform werden durch die Konfiguration des Projekts gespeichert, in der aktiven Projektmappenkonfiguration bestimmt. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Methode kann verwendet werden, um die aktive Projektkonfiguration abzurufen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objekt kann optional implementiert werden, auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> -Objekt mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> Objekt, das Sie abrufen können eine `IVsProjectCfg2` -Objekts basierend auf den Namen der kanonische Projektkonfiguration.  
  
 Eine andere Möglichkeit, geben Sie die Umgebung als auch andere Projekte mit Zugriff auf Projektkonfigurationen für Projekte, die eine Implementierung bereitstellen ist die `IVsCfgProvider2::GetCfgs` Methode, um eine oder mehrere Konfigurationsobjekte zurückzugeben. Projekte können auch implementieren, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, erbt die `IVsProjectCfg` und somit von `IVsCfg`, damit die Konfiguration-spezifische Informationen. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> unterstützt die Plattformen und Funktionen zum Hinzufügen, löschen und Umbenennen von Projektkonfigurationen.  
  
> [!NOTE]
>  Seit Visual Studio nicht mehr auf zwei Konfigurationstypen beschränkt ist, Code, der verarbeitet Konfigurationen nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden sollten, und unter der Annahme geschrieben werden, ein Projekt, das nur eine Festplatte verfügt Konfiguration ist unbedingt entweder "Debug" oder "Retail. Dadurch wird die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> veraltet.  
  
 Aufrufen von `QueryInterface` auf das Objekt, das von`IVsGetCfgProvider::GetCfgProvider` ruft `IVsCfgProvider2`. Wenn `IVsGetCfgProvider` befindet sich nicht durch den Aufruf `QueryInterface` auf die `IVsProject3` Projekt-Objekts können Sie erreichen das konfigurationsanbieterobjekt durch Aufrufen von `QueryInterface` für die Hierarchie Browser Stammobjekt für das Objekt zurückgegeben, die für `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, oder über Ein Zeiger auf den Konfigurationsanbieter für zurückgegebene `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` in erster Linie ermöglicht den Zugriff auf "erstellen", Debuggen und Bereitstellungsobjekte für die Verwaltung und Projekte die Freiheit gibt, Gruppe Ausgaben. Die Methoden der `IVsProjectCfg` und `IVsProjectCfg2` kann verwendet werden, um implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> zum Verwalten des Buildprozesses nimmt und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Zeiger für die Ausgabegruppen einer Konfiguration.  
  
 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration zurückgeben, die es unterstützt, obwohl die Anzahl von Ausgaben in einer Gruppe enthaltene aus Konfiguration variieren kann. Die Gruppen müssen auch den gleichen Bezeichnerinformationen (kanonische Name, Anzeigename und Gruppeninformationen) von Konfiguration innerhalb eines Projekts haben. Weitere Informationen finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
 Zum Aktivieren des Debuggens, sollte Ihre Konfigurationen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` ist eine optionale Schnittstelle implementiert von Datenbankprojekten, um den Debugger an eine Konfiguration starten können, und wird auf das Konfigurationsobjekt mit implementiert `IVsCfg` und `IVsProjectCfg`. Die Umgebung ruft es, wenn der Benutzer entscheidet, um den Debugger durch Drücken von F5 zu starten.  
  
 `ISpecifyPropertyPages` und `IDispatch` werden zusammen mit Eigenschaftenseiten abrufen und Anzeigen von konfigurationsabhängigen Informationen für den Benutzer verwendet. Weitere Informationen finden Sie unter [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md)   
 [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)