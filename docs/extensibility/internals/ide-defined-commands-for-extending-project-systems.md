---
title: IDE-definierte Befehle zum Erweitern von Projektsystemen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132014"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE-definierte Befehle zum Erweitern von Projektsystemen
Wenn Sie Projektsystemen erweitern möchten, können Sie Befehle verwenden und Gruppen bereitgestellt, die vom Befehl die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 In den folgenden Abschnitten Listenelemente Befehl, die zum Erweitern von Projektsystemen besonders nützlich sind.  
  
## <a name="command-menus"></a>Befehlsmenüs  
 Die folgende Tabelle zeigt die Befehlsmenüs, die sind hilfreich für Sie allgemeine Befehle hinzufügen, mit die einen Projekt Extender aufgerufen.  
  
|Befehlsmenü|Beschreibung|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Die **Projekt** Menü der obersten Ebene.|  
|IDM_VS_TOOL_PROJWIN|Die **Projektmappen-Explorer** Symbolleiste.|  
  
## <a name="shortcut-menus"></a>Kontextmenüs  
 Die folgende Tabelle zeigt die Kontextmenüs, die gelten, wenn in ein einzelnen Knoten ausgewählt ist die **Projektmappen-Explorer**, oder wenn es homogenen Mehrfachauswahl in der **Projektmappen-Explorer**, also wenn alle ausgewählten Knoten sind vom gleichen Typ.  
  
|Kontextmenü|Beschreibung|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Gilt, wenn Sie der Projektknoten ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Gilt, wenn eine Datei ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Gilt, wenn Sie ein Ordner ausgewählt ist.|  
|IDM_VS_CTXT_WEBREFFOLDER|Gilt, wenn der Ordner "Webverweis" ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Gilt, wenn der Knoten "Verweise Root" namens "Verweise" ausgewählt ist.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Gilt, wenn Verweisknoten ausgewählt werden; Dazu gehören Assembly COM-Assemblys und nur die Projektverweise. Webverweise enthält keine werden.|  
  
 Die folgende Tabelle zeigt die Kontextmenüs, die beim Anwenden der Auswahl in der **Projektmappen-Explorer** erstreckt sich über mehrere Hierarchien  
  
|Kontextmenü|Beschreibung|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Gilt, wenn die aktuelle Auswahl der Knoten "Projektmappe" und der Stammknoten-Projekt enthält.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Gilt, wenn die aktuelle Auswahl Projektmappenelemente Knoten und das Projekt enthält.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Gilt, wenn mehrere Projekt Stammknoten nur die aktuelle Auswahl besteht.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Gilt, wenn die aktuelle Auswahl eine Mischung aus Projekt Stammknoten und Projektelemente enthält. Darüber hinaus kann die Auswahl der Knoten "Projektmappe" enthalten.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Gilt, wenn die aktuelle Auswahl Projektelemente aus in der Projektmappe mehrere Projekte enthält, oder wenn Elemente unterschiedlichen Typs im selben Projekt ausgewählt sind.|  
  
## <a name="command-groups"></a>Befehlsgruppen  
 Die folgende Tabelle zeigt die Befehlsgruppen, die Sie verwenden können, wenn Sie Projekte erweitern und die Sie zugreifen können, durch die <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> Kontextmenü.  
  
|Befehlsgruppe|Beschreibung|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Befehle zum Erstellen, neu erstellen und Bereitstellen des Projekts.|  
|IDG_VS_CTXT_COMPILELINK|Befehle zum Kompilieren und verknüpfen das Projekt.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Befehle, die Projektkonfiguration festgelegt und Buildreihenfolge.|  
|IDG_VS_CTXT_PROJECT_ADD|Befehle, die dem Projekt Elemente hinzu.|  
|IDG_VS_CTXT_PROJECT_START|Befehle, die das zugeordnete der F5-Taste Startprojekt festzulegen.|  
|IDG_VS_CTXT_PROJECT_SAVE|Befehle für die Speicherung von Projektelementen.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Befehle für das Debuggen.|  
|IDG_VS_CTXT_PROJECT_SCC|Befehle für die Datenquellen-Steuerelements.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Befehle zum Ausschneiden, kopieren und einfügen.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Befehle, die Zugriff auf die **Projekteigenschaften** (Dialogfeld).|  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md)