---
title: "Projekt-Konfigurationsobjekt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektkonfigurationen, Objekt"
  - "Objekte, die Konfiguration des Projekts"
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Projekt-Konfigurationsobjekt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Konfigurationsobjekt Projekt verwaltet die Anzeige der Konfigurationsinformationen auf der Benutzeroberfläche.  
  
 ![Visual Studio&#45;Projektkonfiguration](~/extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Eigenschaftenseiten für Projekt\-Konfiguration  
  
 Der Konfigurationsanbieter Projekt verwaltet die Projektkonfigurationen. Die Umgebung und andere Pakete zugreifen und Abrufen von Informationen zu Konfigurationen eines Projekts, die Projekt Konfigurationsanbieter Objekt zugeordneten Schnittstellen aufzurufen.  
  
> [!NOTE]
>  Sie können nicht erstellen oder bearbeiten die Konfigurationsdateien für die Lösung programmgesteuert. Verwenden Sie `DTE.SolutionBuilder`. Weitere Informationen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
 Zum Veröffentlichen eines Anzeigenamen in der Konfigurations\-UI verwendet werden, sollte das Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, womit eine Liste der `IVsCfg` Zeiger, die Sie verwenden können, zum Abrufen der Anzeigenamen für die Konfiguration und Plattform\-Informationen in der Umgebung Benutzeroberfläche aufgeführt werden. Die aktive Konfiguration und Plattform ergeben sich die Konfiguration des Projekts in der aktiven Projektmappenkonfiguration gespeichert. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Methode kann verwendet werden, um die aktive Projektkonfiguration abzurufen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objekt kann optional implementiert werden, auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> \-Objekt mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> \-Objekt, das Sie abrufen können ein `IVsProjectCfg2` \-Objekt basierend auf den Namen der Projektkonfiguration kanonische.  
  
 Eine andere Möglichkeit, Zugriff auf Konfigurationen der Umgebung und anderen Projekten ermöglichen ist für Projekte, die eine Implementierung bereitstellen der `IVsCfgProvider2::GetCfgs` Methode, um ein oder mehrere Objekte zurückzugeben. Projekte können auch implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, erbt von `IVsProjectCfg` und somit von `IVsCfg`, Konfigurations\-spezifische Informationen bereitzustellen.<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> unterstützt die Plattformen und Funktionen zum Hinzufügen, löschen und Umbenennen von Projektkonfigurationen.  
  
> [!NOTE]
>  Seit Visual Studio nicht mehr auf zwei Konfigurationstypen beschränkt ist, Code, der verarbeitet Konfigurationen sollten nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden, noch sollte er geschrieben werden unter der Annahme, der ein Projekt, das nur eine Konfiguration ist unbedingt Debug\- oder Verkaufsbuild. Dadurch wird die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> veraltet.  
  
 Aufrufen von `QueryInterface` auf das von zurückgegebene Objekt`IVsGetCfgProvider::GetCfgProvider` ruft `IVsCfgProvider2`. Wenn `IVsGetCfgProvider` nicht gefunden wird, durch Aufrufen von `QueryInterface` auf die `IVsProject3` Project\-Objekt, Sie können das Konfigurationsobjekt für den Anbieter zugreifen, durch Aufrufen von `QueryInterface` für die Hierarchie Browser Stammobjekt für das Objekt zurückgegeben `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, oder über einen Zeiger auf den Konfigurationsanbieter für zurückgegeben `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` vor allem bietet Zugriff auf entwickeln, Debuggen und Bereitstellung von Verwaltungsobjekten und können Projekte die Freiheit, Gruppe Ausgaben. Die Methoden der `IVsProjectCfg` und `IVsProjectCfg2` kann verwendet werden, um implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> des Buildprozesses zu verwalten und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Zeiger für die Ausgabegruppen für eine Konfiguration.  
  
 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration zurückgeben, die er unterstützt, obwohl die Anzahl von Ausgaben in einer Gruppe enthaltene aus Konfiguration variieren. Die Gruppen müssen auch die gleichen ID\-Informationen \(kanonische Name, Anzeigename und Gruppeninformationen\) von Konfiguration innerhalb eines Projekts haben. Weitere Informationen finden Sie unter [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md).  
  
 Zum Aktivieren des Debuggens, sollten Ihre Konfigurationen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.`IVsDebuggableProjectCfg` ist eine optionale Schnittstelle, die von Projekten zu eine Konfiguration starten der Debugger kann implementiert und wird auf das Konfigurationsobjekt mit implementiert `IVsCfg` und `IVsProjectCfg`. Die Umgebung ruft es, wenn der Benutzer entscheidet, um den Debugger zu starten, indem Sie F5 drücken.  
  
 `ISpecifyPropertyPages` und `IDispatch` werden zusammen mit Eigenschaftenseiten abrufen und Anzeigen von konfigurationsabhängig Informationen für den Benutzer verwendet. Weitere Informationen finden Sie unter [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
## Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration zum Erstellen des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md)   
 [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)