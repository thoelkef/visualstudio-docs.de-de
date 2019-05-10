---
title: Erweitern von Menüs und Befehlen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962037"
---
# <a name="extending-menus-and-commands"></a>Erweitern von Menüs und Befehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Befehle sind die Möglichkeit, die Sie Aktionen und Prozesse zu Visual Studio hinzufügen. In den meisten Fällen werden die Befehle in Menüs oder Symbolleisten angezeigt. VSPackage-Projektvorlage veranschaulicht einen einfachen Befehl zu implementieren. Eine Implementierung etwas länger, aber immer noch grundlegenden finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu Visual Studio-Befehle, Menüs und Symbolleisten finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Befehle, Menüs und Symbolleisten sind in der VSCT-Datei definiert, die Teil des VSPackage-Projekten. Sie finden Informationen zu Visual Studio-IDE und die VSCT-Datei im [wie VSPackages hinzufügen Benutzeroberflächenelemente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 In den folgenden Themen wird erläutert, wie verschiedene Arten von Befehle, Menüs und Symbolleisten hinzufügen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Es wird erläutert, wie ein Menü der obersten Visual Studio-Menüleiste hinzuzufügen.  
  
 [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Erläutert, wie eine Tastenkombination (z. B. STRG + 3) ein Menüelement hinzu.  
  
 [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)  
 Erläutert, wie im oberen Menü ein Untermenü hinzugefügt.  
  
 [Hinzufügen einer Liste „Zuletzt verwendet“ zu einem Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Es wird erläutert, wie eine zuletzt verwendet-Liste hinzufügen.  
  
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md)  
 Beschreibt das Befehl-Elemente zu gruppieren, sodass sie in mehreren Menüs aufgenommen werden können.  
  
 [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
 Beschreibt, wie Sie einen Befehl auf eine Symbolleiste und ein Menü ein Symbol hinzu.  
  
 [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
 Beschreibt die Verwendung von der `TextChanges` Kennzeichnung zum Aktivieren eines Menüelements dynamisch geändert werden.  
  
 [Ändern der Darstellung eines Befehls](../extensibility/changing-the-appearance-of-a-command.md)  
 Beschreibt, wie dynamisch aktivieren oder deaktivieren einen Befehl.  
  
 [Aktualisieren der Benutzeroberfläche](../extensibility/updating-the-user-interface.md)  
 Beschreibt, wie eine Aktualisierung der Benutzeroberfläche entsprechend der zuletzt vorgenommenen Änderungen zu erzwingen.  
  
 [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)  
 Erläutert, wie zum Lokalisieren von Menübefehlen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte
