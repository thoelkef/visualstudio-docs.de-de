---
title: Projekt Konfigurationsobjekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725840"
---
# <a name="project-configuration-object"></a>Projektkonfigurationsobjekt
Das Projekt Konfigurationsobjekt verwaltet die Anzeige der Konfigurationsinformationen für die Benutzeroberfläche.

 ![Visual Studio-Projekt Konfiguration](../../extensibility/internals/media/vsprojectcfg.gif "vsprojectcfg") Eigenschaften Seiten für die Projekt Konfiguration

 Der Projekt Konfigurations Anbieter verwaltet die Projekt Konfigurationen. Die Umgebung und andere Pakete, um Zugriff auf die und das Abrufen von Informationen über die Konfigurationen eines Projekts zu erhalten, rufen Sie die Schnittstellen auf, die an das Projekt Konfigurations Anbieter Objekt angefügt

> [!NOTE]
> Projektmappenkonfigurationsdateien können nicht Programm gesteuert erstellt oder bearbeitet werden. Hierzu muss `DTE.SolutionBuilder` verwendet werden. Weitere  Informationen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).

 Um einen anzeigen Amen zu veröffentlichen, der in der Konfigurations Benutzeroberfläche verwendet werden soll, sollte das Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>implementieren. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>auf, die eine Liste mit `IVsCfg` Zeigern zurückgibt, die Sie verwenden können, um die anzeigen Amen für die Konfigurations-und Platt Form Informationen zu erhalten, die in der Benutzeroberfläche der Umgebung aufgelistet werden sollen. Die aktive Konfiguration und Plattform werden durch die Konfiguration des Projekts festgelegt, die in der aktiven Projektmappenkonfiguration gespeichert ist. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>-Methode kann verwendet werden, um die aktive Projekt Konfiguration abzurufen.

 Das <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>-Objekt kann optional für das <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>-Objekt mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>-Objekt implementiert werden, damit Sie ein `IVsProjectCfg2` Objekt basierend auf dem Namen der kanonischen Projekt Konfiguration abrufen können.

 Eine andere Möglichkeit, die Umgebung und andere Projekte mit Zugriff auf Projekt Konfigurationen bereitzustellen, besteht darin, dass Projekte eine Implementierung der `IVsCfgProvider2::GetCfgs`-Methode bereitstellen, um mindestens ein Konfigurationsobjekt zurückzugeben. Die Projekte können auch <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>implementieren, die von `IVsProjectCfg` und somit von `IVsCfg`erbt, um Konfigurations spezifische Informationen bereitzustellen. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> unterstützt Plattformen und Funktionen zum Hinzufügen, löschen und Umbenennen von Projekt Konfigurationen.

> [!NOTE]
> Da Visual Studio nicht mehr auf zwei Konfigurationstypen beschränkt ist, sollte der Code, der Konfigurationen verarbeitet, nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden, und er sollte nicht mit der Annahme geschrieben werden, dass ein Projekt mit nur einem die Konfiguration ist notwendigerweise entweder Debug oder Retail. Dadurch wird die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> als veraltet eingestuft.

 Das Aufrufen von `QueryInterface` für das von`IVsGetCfgProvider::GetCfgProvider` zurückgegebene Objekt ruft `IVsCfgProvider2`ab. Wenn `IVsGetCfgProvider` nicht gefunden wird, indem `QueryInterface` für das `IVsProject3` Project-Objekt aufgerufen wird, können Sie auf das Konfigurations Anbieter Objekt zugreifen, indem Sie `QueryInterface` für das Hierarchie Stamm Browser-Objekt für das Objekt aufrufen, das für `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`zurückgegeben wurde, oder durch einen Zeiger auf das der Konfigurations Anbieter wurde für `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`zurückgegeben.

 `IVsProjectCfg2` bietet hauptsächlich Zugriff auf Build-, Debug-und bereitstellungsverwaltungsobjekte und ermöglicht es Projekten, Ausgaben zu gruppieren. Die Methoden von `IVsProjectCfg` und `IVsProjectCfg2` können verwendet werden, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> zum Verwalten des Buildprozesses zu implementieren, und <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Zeiger für die Ausgabe Gruppen einer Konfiguration.

 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration zurückgeben, die unterstützt wird, obwohl die Anzahl der in einer Gruppe enthaltenen Ausgaben von der Konfiguration bis zur Konfiguration abweichen kann. Die Gruppen müssen auch die gleichen Bezeichnerinformationen (Kanonischer Name, Anzeige Name und Gruppeninformationen) aufweisen, von der Konfiguration bis zur Konfiguration innerhalb eines Projekts. Weitere Informationen finden Sie unter [Projekt Konfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

 Um das Debuggen zu aktivieren, sollten Ihre Konfigurationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>implementieren. `IVsDebuggableProjectCfg` ist eine optionale, von Projekten implementierte Schnittstelle, die es dem Debugger ermöglicht, eine Konfiguration zu starten, und wird auf dem Konfigurationsobjekt mit `IVsCfg` und `IVsProjectCfg`implementiert. Die Umgebung ruft Sie auf, wenn der Benutzer die Option zum Starten des Debuggers durch Drücken von F5 wählt.

 `ISpecifyPropertyPages` und `IDispatch` werden zusammen mit Eigenschaften Seiten verwendet, um dem Benutzer Konfigurations abhängige Informationen abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Eigenschaften Seiten](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Siehe auch
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
- [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)