---
title: Konfigurationsobjekts für das Projekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d84dd905c09b0bcc19833198b925f66dea245b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958820"
---
# <a name="project-configuration-object"></a>Projektkonfigurationsobjekt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dem projektkonfigurationsobjekt verwaltet es sich um die Anzeige der Konfigurationsinformationen auf der Benutzeroberfläche.  
  
 ![Visual Studio-Projektkonfiguration](../../extensibility/internals/media/vsprojectcfg.gif "VsProjectCfg")  
Eigenschaftenseiten für Projekt-Konfiguration  
  
 Der Konfigurationsanbieter Projekt verwaltet die Projektkonfigurationen. Die Umgebung und andere Pakete, auf das Abrufen von Informationen zu Konfigurationen eines Projekts, und rufen Sie die Projekt-Konfigurationsanbieter-Objekt zugeordneten Schnittstellen zuzugreifen.  
  
> [!NOTE]
>  Sie können nicht erstellen oder bearbeiten die Konfigurationsdateien für die Lösung programmgesteuert. Verwenden Sie `DTE.SolutionBuilder`. Finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md) für Weitere Informationen.  
  
 Um veröffentlichen einen Anzeigenamen ein, in der Benutzeroberfläche für die Konfiguration verwendet werden, sollte Ihr Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, womit eine Liste der `IVsCfg` Zeiger, die Sie verwenden können, zum Abrufen der Anzeigenamen für die Konfiguration und Plattform-Informationen in der Benutzeroberfläche der Umgebung aufgelistet werden. Die aktive Konfiguration und Plattform ergeben sich die Konfiguration des Projekts in der Konfiguration der aktuellen Projektmappe gespeichert. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Methode kann verwendet werden, um die aktive Projektkonfiguration abzurufen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objekt kann optional implementiert werden, auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> Objekt mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> Objekt, das Sie abrufen können eine `IVsProjectCfg2` -Objekt basierend auf den Namen der kanonische Projektkonfiguration.  
  
 Eine weitere Möglichkeit für die Umgebung und andere Projekte den Zugriff auf Projektkonfigurationen bereit ist für Projekte, die eine Implementierung bereitstellen der `IVsCfgProvider2::GetCfgs` Methode, um eine oder mehrere Konfigurationsobjekte zurück. Die Projekte können auch implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, erbt von `IVsProjectCfg` und dadurch `IVsCfg`, um die konfigurationsspezifischen Informationen bereitstellen. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> unterstützt die Plattformen und Funktionen zum Hinzufügen, löschen und Umbenennen von Projektkonfigurationen.  
  
> [!NOTE]
>  Da Visual Studio nicht mehr auf zwei Arten der Konfiguration beschränkt ist, Code, der Konfigurationen verarbeitet nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden sollte, noch mit der Annahme geschrieben werden, die ein Projekt, das nur eine Festplatte verfügt Konfiguration ist unbedingt Debuggen oder der Verkaufsversion durchführen. Dadurch wird die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> veraltet.  
  
 Aufrufen von `QueryInterface` auf das von zurückgegebene Objekt`IVsGetCfgProvider::GetCfgProvider` ruft `IVsCfgProvider2`. Wenn `IVsGetCfgProvider` wurde nicht gefunden, durch den Aufruf `QueryInterface` auf die `IVsProject3` Project-Objekt, Sie können das konfigurationsanbieterobjekt zugreifen, durch den Aufruf `QueryInterface` für die Hierarchie Browser Stammobjekt für das Objekt zurückgegeben, für die `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, oder über Ein Zeiger auf den Konfigurationsanbieter für zurückgegebenen `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` vor allem bietet Zugriff auf entwickeln, Debuggen und Bereitstellung von Verwaltungsobjekten und können Projekte die Freiheit gibt, die Ausgaben der Gruppe. Die Methoden der `IVsProjectCfg` und `IVsProjectCfg2` kann verwendet werden, um implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> des Buildprozesses zu verwalten und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Zeiger für die Ausgabegruppen einer Konfiguration.  
  
 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration zurückgeben, die es unterstützt, auch wenn die Anzahl von Ausgaben in einer Gruppe enthaltene Konfiguration auf Konfiguration variieren. Die Gruppen müssen auch die gleichen Bezeichnerinformationen (kanonischer Name, Anzeigename und Gruppeninformationen) Konfiguration auf Konfiguration innerhalb eines Projekts verfügen. Weitere Informationen finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
 Zum Debuggen aktivieren möchten, sollten Ihre Konfigurationen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` ist eine optionale Schnittstelle, die von Projekten, damit der Debugger, starten Sie eine Konfiguration kann implementiert und wird auf das Konfigurationsobjekt mit implementiert `IVsCfg` und `IVsProjectCfg`. Die Umgebung ruft es, wenn der Benutzer wählt den Debugger zu starten, indem Sie F5 drücken.  
  
 `ISpecifyPropertyPages` und `IDispatch` werden in Verbindung mithilfe von Eigenschaftenseiten zum Abrufen und Anzeigen der Konfiguration abhängig, die dem Benutzer verwendet. Weitere Informationen finden Sie unter [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md)   
 [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
