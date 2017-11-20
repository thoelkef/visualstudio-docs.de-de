---
title: Eigenschaften und Methoden erweitert, indem Projekt Untertypen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd4e46148950af925b7b41c4e3b5bd66fce5063c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Eigenschaften und Methoden, die vom Projekt Untertypen erweitert
Ein Projektuntertyp hat viel Energie, die das Verhalten des Projekts zu beeinflussen, da er als Aggregator eines Basis-Projekts erstellt wird. Dieser Abschnitt fasst einige der Funktionen, die erweitert oder Untertypen des Projekts geändert werden können.  
  
## <a name="features-gained-by-aggregation"></a>Funktionen, die durch Aggregation erzielt  
 In der folgenden Tabelle werden viele der Methoden, die Aggregation Projekt Untertypen in Basis-Projekten überschreiben ermöglicht es zusammengefasst.  
  
|Methoden, die durch Aggregation überschreiben|Projektuntertyp|  
|---------------------------------------|---------------------|  
|Aus <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Ermöglicht es einen Projektuntertyp<br /><br /> -Ändern Sie Beschriftung und das Symbol der Projektknoten.<br />-Projekt vollständig überschreiben `Browse` Objekt.<br />-Wird gesteuert, ob das Projekt umbenannt werden kann.<br />-Sortierreihenfolge Steuerelement.<br />-Control-Benutzerkontext für die dynamische Hilfe.|  
|Aus <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Können einen Projektuntertyp steuern, welche kontextabhängige Dienste für den Designer und Editoren bereitgestellt werden.|  
|Aus <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Ermöglicht es einen Projektuntertyp<br /><br /> -Befehlsrouting für Befehle teilnehmen.<br />-Hinzufügen, entfernen oder Deaktivieren von Projekt ambient-Befehle und aktive Projektmappen-Explorer-Befehle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Ermöglicht den Untertyp des Projekts zu filtern, sieht der Benutzer in der **neues Element hinzufügen** (Dialogfeld).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Ermöglicht es einen Projektuntertyp<br /><br /> -Bestimmen Sie die Standard-Generator eine Dateierweiterung zugewiesen.<br />-Ein COM-Objekt einen Namen für Menschen lesbaren Generator zuordnen.|  
  
## <a name="properties-used-by-project-subtypes"></a>Eigenschaften, die vom Projekt Untertypen verwendet werden.  
 Das Projektsystem Umgebung und Base mithilfe der Eigenschaften von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> Enumerationen, die in der folgenden Tabelle beschrieben, um einen Projektuntertyp steuern verschiedene Funktionen des Projektsystems zu aktivieren.  
  
|: VSHPROPID-Eigenschaft|Projektuntertyp|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Ermöglicht einen Projektuntertyp steuern den Inhalt der **Element hinzufügen** (Dialogfeld). Untertyp des Projekts geben Sie eine neue Spezifikation der Vorlagenverzeichnisse, neue Arten von Elementen hinzufügen, Entfernen von vorhandenen Elementen und eine Teilmenge der Elemente in der Basis des Projekts reorganize **Element hinzufügen** (Dialogfeld).|  
|`PropertyPagesCLSIDList`|Ermöglicht einen Projektuntertyp hinzufügen oder Entfernen der Konfiguration unabhängig Eigenschaftenseiten.|  
|`CfgPropertyPagesCLSIDList`|Ermöglicht einen Projektuntertyp hinzufügen oder entfernen die konfigurationsabhängigen Eigenschaftenseiten.|  
|`ExtObjectCATID`|Können einen Projektuntertyp einer Automatisierungsextender für das Projekt oder Elementobjekte bereitstellen, indem die CATID Extender kennen. Ein Projektuntertyp kann z. B. eine benutzerdefinierte bereitstellen `Project.Extender("<subtype>")` Objekt.|  
|`BrowseObjectCATID`|Ermöglicht einen Projektuntertyp zu einem Automatisierungsextender für die `Browse` Objekt, indem Sie die CATID Extender kennen. Beispielsweise kann ein Projektuntertyp zusätzliche Eigenschaften für Hinzufügen der <xref:EnvDTE.Project.Properties%2A> Auflistung.|  
|`CfgBrowseObjectCATID`|Können einen Projektuntertyp zum Durchsuchen das Projektobjekt-Konfiguration mit einem Automatisierungsextender bereit. Beispielsweise kann ein Projektuntertyp zusätzliche Eigenschaften für Hinzufügen der <xref:EnvDTE.Configuration.Properties%2A> Auflistung.|  
|`CfgExtObjectCATID`|Können einen Projektuntertyp des Konfigurationsobjekts, das einem Automatisierungsextender bereit.|  
|`DefaultPlatformName`|Ermöglicht einen Projektuntertyp den Plattformnamen für das Projekt Konfigurationsobjekte bestimmen.|  
  
 Die Basis-Projekt stellt eine Standardimplementierung der obigen Eigenschaften bereit. Das Basisprojekt ruft diese durch Aufrufen von `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> im äußersten Projekt Untertyp Untertyp des Projekts, um die Implementierung der Eigenschaften überschreiben und somit ermöglicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)