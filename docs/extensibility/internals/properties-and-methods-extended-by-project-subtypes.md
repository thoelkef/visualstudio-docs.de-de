---
title: "Eigenschaften und Methoden, die vom Projekt Untertypen erweitert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekt-Untertypen, erweiterte Methoden"
  - "Projekt-Untertypen, erweiterte Eigenschaften"
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Eigenschaften und Methoden, die vom Projekt Untertypen erweitert
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekt untertyp hohe Leistungsfähigkeit, hat das Verhalten des Projekts auswirken, da er als Aggregator eines Projekts erstellt wird.  In diesem Abschnitt sind einige Funktionen zusammengefasst, die vom Projekt untertypen erhöht oder geändert werden können.  
  
## Funktionen erhalten durch Aggregation  
 Die folgende Tabelle enthält zahlreiche Methoden zusammengefasst, dass Aggregation Projekt untertypen ermöglicht, in den Basis\-URI Projekten zu überschreiben.  
  
|Methoden überschrieben durch Aggregation|Projekt\-Untertyp|  
|----------------------------------------------|-----------------------|  
|Von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Ermöglicht es einem Projekt auf untertyp<br /><br /> -   Ändern der Titelleiste und Symbol des Projektknotens.<br />-   Vollständig Überschreibungen projekt\- `Browse`\-Objekt.<br />-   Steuert, ob Projekt umbenannt werden kann.<br />-   Sortierreihenfolge des Steuerelements.<br />-   Steuerelement für die dynamische Hilfe Benutzer Elementkontext.|  
|Von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Ermöglicht es einem Projekt untertyp, um zu steuern, welche Dienste Kontext für Designer und Editoren bereitgestellt werden.|  
|Von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Ermöglicht es einem Projekt auf untertyp<br /><br /> -   Nehmen Sie am Befehls routing für Befehle Projekt beteiligt.<br />-   Hinzufügen, Entfernen oder deaktivieren Sie die Ambient\-Eigenschaft Befehle des Projekts und aktive Befehle des Projektmappen\-Explorers.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Ermöglicht es dem Projekt untertyp, um zu filtern, den der Benutzer im Dialogfeld **Neues Element hinzufügen** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Ermöglicht es einem Projekt auf untertyp<br /><br /> -   Bestimmen Sie den standardmäßigen angegebenen Generator eine Dateierweiterung.<br />-   Zuordnen eines für den Benutzer lesbaren Namen der Generator auf ein COM\-Objekt.|  
  
## Eigenschaften von Projekt\-Untertypen  
 Das Projektsystem kann Umgebungs\- und Grundlage der Eigenschaften von <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>\-Enumerationen verwenden, die in der folgenden Tabelle aufgeführten einzeln ein Projekt untertyp zu ermöglichen, verschiedene Features des Projektsystems zu steuern.  
  
|VSHPROPID\-Eigenschaft|Projekt\-Untertyp|  
|----------------------------|-----------------------|  
|`AddItemTemplatesGuid`|Ermöglicht einem Projekt untertyp, um den Inhalt des **Element hinzufügen** Dialogfelds zu steuern.  Der Projekt untertyp kann eine neue Spezifikation von Vorlagen verzeichnissen bereitstellen, neue Arten von Elementen vorhandene Elemente hinzufügen, entfernen und eine Teilmenge der Elemente im Basis\- **Element hinzufügen** Dialogfeld des Projekts reorganisieren.|  
|`PropertyPagesCLSIDList`|Ermöglicht einem Projekt untertyp, um konfigurationsunabhängige Eigenschaftenseiten hinzufügen oder entfernen.|  
|`CfgPropertyPagesCLSIDList`|Ermöglicht einem Projekt untertyp, um anlagenabhängige Eigenschaftenseiten hinzufügen oder entfernen.|  
|`ExtObjectCATID`|Ermöglicht einem Projekt untertyp, um einen Automatisierungsextender für die Konfigurationszeile für ein Projekt bzw. Projektelement Objekte aus dem Kennen des Extenders CATID bereitzustellen.  Beispielsweise kann ein Projekt untertyp ein benutzerdefiniertes `Project.Extender("<subtype>")`\-Objekt bereitstellen.|  
|`BrowseObjectCATID`|Ermöglicht einem Projekt untertyp, um einen Automatisierungsextender für das `Browse`\-Objekt durch das Kennen des Extenders CATID bereitzustellen.  Beispielsweise kann ein Projekt untertyp zusätzliche Eigenschaften der <xref:EnvDTE.Project.Properties%2A>\-Auflistung hinzufügen.|  
|`CfgBrowseObjectCATID`|Ermöglicht einem Projekt untertyp, um einen Automatisierungsextender für die Projektkonfiguration suchobjekt bereitzustellen.  Beispielsweise kann ein Projekt untertyp zusätzliche Eigenschaften der <xref:EnvDTE.Configuration.Properties%2A>\-Auflistung hinzufügen.|  
|`CfgExtObjectCATID`|Ermöglicht einem Projekt untertyp, um einen Automatisierungsextender für das Konfigurationsobjekt bereitzustellen.|  
|`DefaultPlatformName`|Ermöglicht einem Projekt untertyp, um den Plattformnamen für die Konfigurationsobjekte des Projekts zu bestimmen.|  
  
 Das niedrige Projekt stellt eine Standardimplementierung der oben aufgeführten Eigenschaften.  Das niedrige Projekt ruft diese ab, indem `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> im äußersten Projekt untertyp aufruft und somit dem Projekt untertyp die Implementierung der Eigenschaften zu überschreiben.  
  
## Siehe auch  
 [Project Untertypen Design](../../extensibility/internals/project-subtypes-design.md)