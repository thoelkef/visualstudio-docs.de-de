---
title: "Erweitern von Menüs und Befehle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c53f836b6384968bf812ae9ae559a281fda6f13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extending-menus-and-commands"></a>Erweitern von Menüs und Befehle
Befehle sind die Möglichkeit, die Sie Aktionen und Prozesse zu Visual Studio hinzufügen. In den meisten Fällen werden die Befehle in Menüs oder Symbolleisten angezeigt. Die VSPackage-Projektvorlage veranschaulicht, wie einen sehr grundlegenden Befehl zu implementieren. Eine Implementierung, aber etwas länger, weiterhin grundlegende finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu Visual Studio-Befehle, Menüs und Symbolleisten finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Befehle, Menüs und Symbolleisten sind in der VSCT-Datei definiert, die Teil der VSPackage-Projekte ist. Sie können erfahren Sie mehr über Visual Studio-IDE und der VSCT-Datei in [wie VSPackages hinzufügen Benutzeroberflächenelemente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 In den folgenden Themen wird erläutert, wie verschiedene Arten von Befehle, Menüs und Symbolleisten hinzufügen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Erläutert, wie ein Menü der obersten Visual Studio-Menüleiste hinzugefügt.  
  
 [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Erläutert, wie ein Menüelement mit einer Tastenkombination (z. B. STRG + 3) hinzu.  
  
 [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)  
 Erläutert, wie im oberen Menü ein Untermenü hinzugefügt.  
  
 [Hinzufügen einer Liste „Zuletzt verwendet“ zu einem Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Erläutert, wie eine Liste zuletzt verwendeter hinzufügen.  
  
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md)  
 Beschreibt, wie der Befehl-Elemente zu gruppieren, damit sie in mehreren Menüs aufgenommen werden können.  
  
 [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
 Beschreibt, wie ein Befehl für eine Symbolleiste und ein Menü ein Symbol hinzu.  
  
 [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
 Beschreibt die Verwendung von der `TextChanges` Kennzeichnung zum Aktivieren eines Menüelements dynamisch geändert werden.  
  
 [Ändern der Darstellung eines Befehls](../extensibility/changing-the-appearance-of-a-command.md)  
 Beschreibt, wie dynamisch aktivieren oder deaktivieren einen Befehl.  
  
 [Aktualisieren der Benutzeroberfläche](../extensibility/updating-the-user-interface.md)  
 Beschreibt, wie eine Aktualisierung der Benutzeroberfläche entsprechend der zuletzt vorgenommenen Änderungen zu erzwingen.  
  
 [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)  
 Erläutert, wie zum Lokalisieren von Menübefehlen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte