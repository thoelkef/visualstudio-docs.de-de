---
title: IDE-definierte Befehle zum Erweitern von Projektsystemen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707737"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE-definierte Befehle zum Erweitern von Projektsystemen
Wenn Sie Projektsysteme erweitern möchten, können Sie Befehle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Befehlsgruppen verwenden, die von der IDE bereitgestellt werden.

 In den folgenden Abschnitten werden Befehlselemente aufgeführt, die besonders zum Erweitern von Projektsystemen nützlich sind.

## <a name="command-menus"></a>Befehlsmenüs
 Die folgende Tabelle zeigt die Befehlsmenüs, die nützliche Speicherorte für das Setzen von Befehlen auf hoher Ebene sind, die einen Projekt-Extender aufrufen.

|Befehlsmenü|BESCHREIBUNG|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Das Menü der obersten Ebene des **Projekts.**|
|IDM_VS_TOOL_PROJWIN|Die **Symbolleiste des Projektmappen-Explorers.**|

## <a name="shortcut-menus"></a>Kontextmenüs
 Die folgende Tabelle zeigt die Kontextmenüs, die gelten, wenn ein einzelner Knoten im **Projektmappen-Explorer**ausgewählt ist oder wenn im **Projektmappen-Explorer**mehrere homogene Auswahlen vorhanden sind, wenn alle ausgewählten Knoten vom gleichen Typ sind.

|Shortcut-Menü|BESCHREIBUNG|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Gilt, wenn der Projektknoten ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Gilt, wenn eine Datei ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Gilt, wenn ein Ordner ausgewählt ist.|
|IDM_VS_CTXT_WEBREFFOLDER|Gilt, wenn der Webreferenzordner ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Gilt, wenn der Referenzstammknoten mit dem Namen "Referenzen" ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Gilt, wenn Referenzknoten ausgewählt sind; Dazu gehören nur Assembly-, COM- und Projektverweise. Enthält keine Webverweise.|

 Die folgende Tabelle zeigt die Kontextmenüs, die gelten, wenn die Auswahl im **Projektmappen-Explorer** mehrere Hierarchien umfasst,

|Shortcut-Menü|BESCHREIBUNG|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Gilt, wenn die aktuelle Auswahl den Projektmappenknoten und Stammprojektknoten enthält.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Gilt, wenn die aktuelle Auswahl den Projektmappenknoten und Projektelemente enthält.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Gilt, wenn die aktuelle Auswahl nur aus mehreren Stammprojektknoten besteht.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Gilt, wenn die aktuelle Auswahl eine Mischung aus Stammprojektknoten und Projektelementen enthält. Darüber hinaus kann die Auswahl den Lösungsknoten enthalten.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Gilt, wenn die aktuelle Auswahl Projektelemente aus mehreren Projekten in der Projektmappe enthält oder wenn Elemente unterschiedlicher Typen im selben Projekt ausgewählt werden.|

## <a name="command-groups"></a>Befehlsgruppen
 Die folgende Tabelle zeigt die Befehlsgruppen, die Sie beim Erweitern <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> von Projekten verwenden können und auf die Sie über das Kontextmenü zugreifen können.

|Befehlsgruppe|BESCHREIBUNG|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Befehle zum Erstellen, Neuaufbau und Bereitstellen des Projekts.|
|IDG_VS_CTXT_COMPILELINK|Befehle zum Kompilieren und Verknüpfen des Projekts.|
|IDG_VS_CTXT_PROJECT_CONFIG|Befehle, die die Projektkonfiguration und die Buildreihenfolge festlegen.|
|IDG_VS_CTXT_PROJECT_ADD|Befehle, die dem Projekt Elemente hinzufügen.|
|IDG_VS_CTXT_PROJECT_START|Befehle, die das Startprojekt festlegen, das der F5-Taste zugeordnet ist.|
|IDG_VS_CTXT_PROJECT_SAVE|Befehle zum Speichern von Projektelementen.|
|IDG_VS_CTXT_PROJECT_DEBUG|Befehle zum Debuggen.|
|IDG_VS_CTXT_PROJECT_SCC|Befehle für die Quellcodeverwaltung.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Befehle für Ausschneiden, Kopieren und Einfügen von Vorgängen.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Befehle, die Zugriff auf das Dialogfeld **Projekteigenschaften** ermöglichen.|

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md)
