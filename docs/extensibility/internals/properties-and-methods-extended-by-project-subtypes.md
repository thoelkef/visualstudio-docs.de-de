---
title: Eigenschaften und Methoden, die von Projekt Untertypen erweitert werden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725342"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Eigenschaften und Methoden, die von Projektuntertypen erweitert werden
Ein Projekt Untertyp verfügt über viele Möglichkeiten, das Verhalten des Projekts zu beeinflussen, da es als Aggregator eines Basis Projekts erstellt wird. In diesem Abschnitt werden einige der Funktionen zusammengefasst, die von Projekt Untertypen erweitert oder geändert werden können.

## <a name="features-gained-by-aggregation"></a>Von der Aggregation ergewonnene Features
 In der folgenden Tabelle werden viele der Methoden zusammengefasst, die die Aggregation von Projekt Untertypen in Basisprojekten ermöglicht.

|Durch Aggregation überschriebene Methoden|Projekt Untertyp|
|---------------------------------------|---------------------|
|Aus <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Ermöglicht einem Projekt Untertyp das<br /><br /> -Ändern Sie die Beschriftung und das Symbol des Projekt Knotens.<br />-Projekt `Browse`-Objekt vollständig überschreiben.<br />-Steuern Sie, ob das Projekt umbenannt werden kann.<br />-Steuerelement Sortierreihenfolge.<br />-Steuern Sie den Benutzer Kontext für die dynamische Hilfe.|
|Aus <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Ermöglicht einem Projekt Untertyp, zu steuern, welche Kontext Dienste für Designer und Editoren bereitgestellt werden.|
|Aus <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Ermöglicht einem Projekt Untertyp das<br /><br /> -Nehmen Sie an der Befehls Weiterleitung für Projekt Befehle Teil.<br />-Hinzufügen, entfernen oder Deaktivieren von Project Ambient-Befehlen und Projektmappen-Explorer aktiven Befehlen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Ermöglicht dem Projekt Untertyp das Filtern, was dem Benutzer im Dialogfeld **Neues Element hinzufügen** angezeigt wird.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Ermöglicht einem Projekt Untertyp das<br /><br /> -Ermitteln des Standard Generators, wenn eine Dateierweiterung angegeben ist.<br />-Ordnen Sie einem COM-Objekt einen lesbaren Generator Namen zu.|

## <a name="properties-used-by-project-subtypes"></a>Eigenschaften, die von Projekt Untertypen verwendet werden
 Die Umgebung und das Basisprojekt System können die Eigenschaften aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> Enumerationen verwenden, die in der folgenden Tabelle beschrieben werden, um einen Projekt Untertyp zum Steuern verschiedener Funktionen des Projekt Systems zu aktivieren.

|Vshpropid-Eigenschaft|Projekt Untertyp|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Ermöglicht einem Projekt Untertyp, den Inhalt des Dialog Felds **Element hinzufügen** zu steuern. Der Projekt Untertyp kann eine neue Spezifikation für Vorlagen Verzeichnisse bereitstellen, neue Arten von Elementen hinzufügen, vorhandene Elemente entfernen und eine Teilmenge der Elemente im Dialogfeld **Element hinzufügen** des Basis Projekts neu organisieren.|
|`PropertyPagesCLSIDList`|Ermöglicht einem Projekt Untertyp das Hinzufügen oder Entfernen von Konfigurations unabhängigen Eigenschaften Seiten.|
|`CfgPropertyPagesCLSIDList`|Ermöglicht einem Projekt Untertyp das Hinzufügen oder Entfernen von Konfigurations abhängigen Eigenschaften Seiten.|
|`ExtObjectCATID`|Ermöglicht einem Projekt Untertyp, einen Automatisierungsextender für die Projekt-oder Projekt Element Objekte bereitzustellen, indem der Extender-CATID bekannt ist. Beispielsweise kann ein Projekt Untertyp ein benutzerdefiniertes `Project.Extender("<subtype>")` Objekt bereitstellen.|
|`BrowseObjectCATID`|Ermöglicht einem Projekt Untertyp, einen Automatisierungsextender für das `Browse` Objekt bereitzustellen, indem der Extender-CATID bekannt ist. Beispielsweise können mit einem Projekt Untertyp der <xref:EnvDTE.Project.Properties%2A> Auflistung zusätzliche Eigenschaften hinzugefügt werden.|
|`CfgBrowseObjectCATID`|Ermöglicht einem Projekt Untertyp das Bereitstellen eines Automatisierungsextenders für das Projekt Konfigurations Such Objekt. Beispielsweise können mit einem Projekt Untertyp der <xref:EnvDTE.Configuration.Properties%2A> Auflistung zusätzliche Eigenschaften hinzugefügt werden.|
|`CfgExtObjectCATID`|Ermöglicht einem Projekt Untertyp, einen Automatisierungsextender für das Konfigurationsobjekt bereitzustellen.|
|`DefaultPlatformName`|Ermöglicht einem Projekt Untertyp, den Platt Form Namen für die Konfigurationsobjekte des Projekts zu bestimmen.|

 Das Basisprojekt stellt eine Standard Implementierung der obigen Eigenschaften bereit. Das Basisprojekt ruft diese durch Aufrufen von `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> im äußersten Projekt Untertyp ab und ermöglicht so dem Projekt Untertyp, die Implementierung der Eigenschaften zu überschreiben.

## <a name="see-also"></a>Siehe auch
- [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)