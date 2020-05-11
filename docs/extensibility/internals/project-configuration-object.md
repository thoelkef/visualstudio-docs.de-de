---
title: Projektkonfigurationsobjekt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706657"
---
# <a name="project-configuration-object"></a>Projektkonfigurationsobjekt
Das Projektkonfigurationsobjekt verwaltet die Anzeige von Konfigurationsinformationen auf der Benutzeroberfläche.

 ![Visual Studio-Projektkonfiguration](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Eigenschaftenseiten für die Projektkonfiguration

 Der Projektkonfigurationsanbieter verwaltet die Projektkonfigurationen. Die Umgebung und andere Pakete, um Zugriff auf die Konfigurationen eines Projekts zu erhalten und Informationen zu den Konfigurationen eines Projekts abzurufen, rufen Sie die Schnittstellen auf, die an das Projektkonfigurationsanbieterobjekt angefügt sind.

> [!NOTE]
> Sie können Lösungskonfigurationsdateien nicht programmgesteuert erstellen oder bearbeiten. Hierzu muss `DTE.SolutionBuilder` verwendet werden. Weitere Informationen finden Sie unter [Lösungskonfiguration.](../../extensibility/internals/solution-configuration.md)

 Um einen Anzeigenamen zu veröffentlichen, der in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>Konfigurationsbenutzeroberfläche verwendet werden soll, sollte das Projekt implementieren. Die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>ruft auf , `IVsCfg` die eine Liste von Zeigern zurückgibt, mit denen Sie die Anzeigenamen für die Konfigurations- und Plattforminformationen abrufen können, die in der Benutzeroberfläche der Umgebung aufgeführt werden sollen. Die aktive Konfiguration und Plattform wird durch die In der aktiven Projektmappe gespeicherte Projektkonfiguration bestimmt. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Methode kann verwendet werden, um die aktive Projektkonfiguration abzurufen.

 Das <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Objekt kann optional für <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> das <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> Objekt mit dem Objekt `IVsProjectCfg2` implementiert werden, damit Sie ein Objekt basierend auf dem kanonischen Projektkonfigurationsnamen abrufen können.

 Eine andere Möglichkeit, der Umgebung und anderen Projekten Zugriff auf Projektkonfigurationen `IVsCfgProvider2::GetCfgs` zu gewähren, besteht darin, dass Projekte eine Implementierung der Methode bereitstellen, um ein oder mehrere Konfigurationsobjekte zurückzugeben. Die Projekte können <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>auch implementieren, `IVsProjectCfg` die von `IVsCfg`und damit von erben, um konfigurationsspezifische Informationen bereitzustellen. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>unterstützt Plattformen und Funktionen zum Hinzufügen, Löschen und Umbenennen von Projektkonfigurationen.

> [!NOTE]
> Da Visual Studio nicht mehr auf zwei Konfigurationstypen beschränkt ist, sollte Code, der Konfigurationen verarbeitet, nicht mit Annahmen über die Anzahl der Konfigurationen geschrieben werden, und es sollte auch nicht mit der Annahme geschrieben werden, dass ein Projekt, das nur über eine Konfiguration verfügt, notwendigerweise entweder Debug oder Retail ist. Dies macht <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> Verwendung und veraltet.

 Aufruf `QueryInterface` des Objekts, das von`IVsGetCfgProvider::GetCfgProvider` Retrieves `IVsCfgProvider2`zurückgegeben wurde. Wenn `IVsGetCfgProvider` `QueryInterface` das `IVsProject3` Projektobjekt nicht aufgerufen wird, können Sie auf `QueryInterface` das Konfigurationsanbieterobjekt zugreifen, indem `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`Sie das Hierarchiestammbrowserobjekt für das `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`für zurückgegebene Objekt aufrufen oder über einen Zeiger auf den Konfigurationsanbieter, der für zurückgegeben wird.

 `IVsProjectCfg2`bietet in erster Linie Zugriff auf Build-, Debug- und Bereitstellungsverwaltungsobjekte und ermöglicht Projekten die Freiheit, Ausgaben zu gruppieren. Die Methoden `IVsProjectCfg` `IVsProjectCfg2` von und können <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> zum Verwalten des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Buildprozesses und Zeiger für die Ausgabegruppen einer Konfiguration verwendet werden.

 Das Projekt muss für jede unterstützte Konfiguration die gleiche Anzahl von Gruppen zurückgeben, auch wenn die Anzahl der in einer Gruppe enthaltenen Ausgaben von Konfiguration zu Konfiguration variieren kann. Die Gruppen müssen auch über dieselben Bezeichnerinformationen (kanonischer Name, Anzeigename und Gruppeninformationen) von der Konfiguration bis zur Konfiguration innerhalb eines Projekts verfügen. Weitere Informationen finden Sie unter [Projektkonfiguration für Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

 Um das Debuggen zu aktivieren, sollten Ihre Konfigurationen implementieren. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`ist eine optionale Schnittstelle, die von Projekten implementiert wird, damit der `IVsCfg` `IVsProjectCfg`Debugger eine Konfiguration starten kann und für das Konfigurationsobjekt mit und implementiert ist. Die Umgebung ruft sie auf, wenn der Benutzer den Debugger durch Drücken von F5 startet.

 `ISpecifyPropertyPages`und `IDispatch` werden in Verbindung mit Eigenschaftenseiten verwendet, um konfigurationsabhängige Informationen für den Benutzer abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
- [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
