---
title: Eigenschaften und Methoden, die durch Projektuntertypen erweitert werden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706194"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Eigenschaften und Methoden, die von Projektuntertypen erweitert werden
Ein Projektuntertyp hat eine Menge Macht, um das Verhalten des Projekts zu beeinflussen, da er als Aggregator eines Basisprojekts erstellt wird. In diesem Abschnitt werden einige der Features zusammengefasst, die durch Projektuntertypen erweitert oder geändert werden können.

## <a name="features-gained-by-aggregation"></a>Durch Aggregation gewonnene Funktionen
 In der folgenden Tabelle werden viele der Methoden zusammengefasst, mit denen die Aggregation projektübergreifende Projektsubtypes in Basisprojekten überschreiben kann.

|Methoden, die durch Aggregation überschrieben werden|Projekt-Untertyp|
|---------------------------------------|---------------------|
|Von: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Ermöglicht einem Projektuntertyp,<br /><br /> - Ändern Sie Beschriftung und Symbol des Projektknotens.<br />- `Browse` Projektobjekt vollständig überschreiben.<br />- Steuern Sie, ob das Projekt umbenannt werden kann.<br />- Steuern Sie die Sortierreihenfolge.<br />- Steuern Sie den Benutzerkontext für dynamische Hilfe.|
|Von: <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Ermöglicht einem Projektuntertyp, zu steuern, welche kontextbezogenen Dienste Designern und Editoren bereitgestellt werden.|
|Von: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Ermöglicht einem Projektuntertyp,<br /><br /> - Nehmen Sie am Befehlsrouting für Projektbefehle teil.<br />- Hinzufügen, Entfernen oder Deaktivieren sowohl der Projektumgebungsbefehle als auch der aktiven Befehle des Projektmappen-Explorers.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Ermöglicht dem Projektuntertyp, zu filtern, was der Benutzer im Dialogfeld **Neues Element hinzufügen** sieht.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Ermöglicht einem Projektuntertyp,<br /><br /> - Bestimmen Sie den Standardgenerator mit einer Dateierweiterung.<br />- Ordnen Sie einem COM-Objekt einen lesbaren Generatornamen zu.|

## <a name="properties-used-by-project-subtypes"></a>Eigenschaften, die von Projektuntertypen verwendet werden
 Das Umgebungs- und Basisprojektsystem <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> kann die in der folgenden Tabelle beschriebenen Eigenschaften und Enumerationen verwenden, damit ein Projektuntertyp verschiedene Features des Projektsystems steuern kann.

|VSHPROPID-Eigenschaft|Projekt-Untertyp|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Ermöglicht einem Projektuntertyp, den Inhalt des Dialogfelds **Element hinzufügen** zu steuern. Der Projektuntertyp kann eine neue Spezifikation von Vorlagenverzeichnissen bereitstellen, neue Arten von Elementen hinzufügen, vorhandene Elemente entfernen und eine Teilmenge der Elemente im Dialogfeld **Element** hinzufügen des Basisprojekts neu organisieren.|
|`PropertyPagesCLSIDList`|Ermöglicht einem Projektuntertyp das Hinzufügen oder Entfernen konfigurationsunabhängiger Eigenschaftenseiten.|
|`CfgPropertyPagesCLSIDList`|Ermöglicht einem Projektuntertyp das Hinzufügen oder Entfernen konfigurationsabhängiger Eigenschaftenseiten.|
|`ExtObjectCATID`|Ermöglicht einem Projektuntertyp die Bereitstellung eines Automation Extenders für die Projekt- oder Projektelementobjekte, indem die Extender-CATID bekannt ist. Ein Projektuntertyp kann z. `Project.Extender("<subtype>")` B. ein benutzerdefiniertes Objekt bereitstellen.|
|`BrowseObjectCATID`|Ermöglicht einem Projektuntertyp, einen Automation `Browse` Extender für das Objekt bereitzustellen, indem er die Extender-CATID kennt. Beispielsweise kann ein Projektuntertyp der <xref:EnvDTE.Project.Properties%2A> Auflistung zusätzliche Eigenschaften hinzufügen.|
|`CfgBrowseObjectCATID`|Ermöglicht einem Projektuntertyp die Bereitstellung eines Automation Extenders für das Suchobjekt der Projektkonfiguration. Beispielsweise kann ein Projektuntertyp der <xref:EnvDTE.Configuration.Properties%2A> Auflistung zusätzliche Eigenschaften hinzufügen.|
|`CfgExtObjectCATID`|Ermöglicht einem Projektuntertyp die Bereitstellung eines Automation Extenders für das Konfigurationsobjekt.|
|`DefaultPlatformName`|Ermöglicht einem Projektuntertyp, den Plattformnamen für die Konfigurationsobjekte des Projekts zu bestimmen.|

 Das Basisprojekt stellt eine Standardimplementierung der oben genannten Eigenschaften bereit. Das Basisprojekt erhält `QueryInterface` diese, indem es den äußersten Projektsubtyp anruft, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sodass der Projektuntertyp die Implementierung der Eigenschaften überschreiben kann.

## <a name="see-also"></a>Weitere Informationen
- [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)
