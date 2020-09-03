---
title: IDE-definierte Befehle zum Erweitern von Projekt Systemen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b5de061449844b87d60d7a700b1e1c22e1e1282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195033"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE-definierte Befehle zum Erweitern von Projektsystemen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie Projektsysteme erweitern möchten, können Sie Befehle und Befehls Gruppen verwenden, die von der IDE bereitgestellt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 In den folgenden Abschnitten werden Befehls Elemente aufgelistet, die für die Erweiterung von Projekt Systemen besonders nützlich sind.  
  
## <a name="command-menus"></a>Befehls Menüs  
 In der folgenden Tabelle sind die Befehls Menüs aufgeführt, die nützliche Orte zum Platzieren von Befehlen auf hoher Ebene sind, die einen Projekt Extender aufrufen.  
  
|Befehlsmenü|Beschreibung|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Das Menü der obersten Ebene des **Projekts** .|  
|IDM_VS_TOOL_PROJWIN|Die **Projektmappen-Explorer** Symbolleiste.|  
  
## <a name="shortcut-menus"></a>Kontextmenüs  
 In der folgenden Tabelle werden die Kontextmenüs angezeigt, die angewendet werden, wenn ein einzelner Knoten im **Projektmappen-Explorer**ausgewählt wird, oder wenn mehrere homogene Optionen in der **Projektmappen-Explorer**vorhanden sind, wenn alle ausgewählten Knoten denselben Typ haben.  
  
|Kontextmenü|Beschreibung|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Gilt, wenn der Projekt Knoten ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Gilt, wenn eine Datei ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Gilt, wenn ein Ordner ausgewählt wird.|  
|IDM_VS_CTXT_WEBREFFOLDER|Gilt, wenn der Webverweis Ordner ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Gilt, wenn der Verweis Stamm Knoten mit dem Namen "References" ausgewählt wird.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Gilt, wenn Verweis Knoten ausgewählt werden. Hierzu gehören nur Assembly-, com-und Projekt Verweise. Enthält keine Webverweise.|  
  
 In der folgenden Tabelle werden die Kontextmenüs angezeigt, die angewendet werden, wenn die Auswahl im **Projektmappen-Explorer** mehrere Hierarchien umfasst.  
  
|Kontextmenü|Beschreibung|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Gilt, wenn die aktuelle Auswahl den Projektmappenknoten und die Stamm Projekt Knoten enthält.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Gilt, wenn die aktuelle Auswahl den Projektmappenknoten und die Projekt Elemente enthält.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Gilt, wenn die aktuelle Auswahl nur aus mehreren Stamm Projekt Knoten besteht.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Gilt, wenn die aktuelle Auswahl eine Mischung aus Stamm Projekt Knoten und Projekt Elementen enthält. Außerdem kann die Auswahl den Projektmappenknoten enthalten.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Gilt, wenn die aktuelle Auswahl Projekt Elemente aus mehreren Projekten in der Projekt Mappe enthält oder wenn Elemente verschiedener Typen im selben Projekt ausgewählt werden.|  
  
## <a name="command-groups"></a>Befehls Gruppen  
 In der folgenden Tabelle sind die Befehls Gruppen aufgeführt, die Sie beim Erweitern von Projekten verwenden können, und auf die Sie über das Kontextmenü zugreifen können <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> .  
  
|Befehlsgruppe|Beschreibung|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Befehle zum Erstellen, Neuerstellen und Bereitstellen des Projekts.|  
|IDG_VS_CTXT_COMPILELINK|Befehle zum Kompilieren und Verknüpfen des Projekts.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Befehle, die die Projekt Konfiguration und die Buildreihenfolge festlegen.|  
|IDG_VS_CTXT_PROJECT_ADD|Befehle, die dem Projekt Elemente hinzufügen.|  
|IDG_VS_CTXT_PROJECT_START|Befehle, die das Startprojekt festlegen, das der F5-Taste zugeordnet ist.|  
|IDG_VS_CTXT_PROJECT_SAVE|Befehle zum Speichern von Projekt Elementen.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Befehle für das Debuggen.|  
|IDG_VS_CTXT_PROJECT_SCC|Befehle für die Quell Code Verwaltung.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Befehle für Ausschneide-, Kopier-und Einfügevorgänge.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Befehle, die Zugriff auf das Dialogfeld " **Projekteigenschaften** " bereitstellen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands im Vergleich zu olemenucommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md)
