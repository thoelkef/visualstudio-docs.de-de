---
title: Erweitern von Menüs und Befehlen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 158759d2511b6ba1209a045a898969fce774e0a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512173"
---
# <a name="extending-menus-and-commands"></a>Erweitern von Menüs und Befehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erweitern von Menüs und Befehlen](https://docs.microsoft.com/visualstudio/extensibility/extending-menus-and-commands).  
  
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

