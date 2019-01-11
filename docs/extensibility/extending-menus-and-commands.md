---
title: Erweitern von Menüs und Befehlen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef32dd2bbc44f784a2faaf6edcafcba96a8f113
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910489"
---
# <a name="extend-menus-and-commands"></a>Erweitern von Menüs und Befehlen
Befehle sind die Möglichkeit, die Sie Aktionen und Prozesse zu Visual Studio hinzufügen. In den meisten Fällen werden die Befehle in Menüs oder Symbolleisten angezeigt. VSPackage-Projektvorlage veranschaulicht einen einfachen Befehl zu implementieren. Eine Implementierung etwas länger, aber immer noch grundlegenden finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu Visual Studio-Befehle, Menüs und Symbolleisten finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Befehle, Menüs und Symbolleisten werden definiert, der *VSCT* Datei, die Teil des VSPackage-Projekten. Sie erhalten Informationen über die Visual Studio-IDE und die *VSCT* Datei [wie VSPackages hinzufügen, Elemente der Benutzeroberfläche](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 In den folgenden Themen wird erläutert, wie verschiedene Arten von Befehle, Menüs und Symbolleisten hinzufügen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen eines Menüs zur Menüleiste Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Es wird erläutert, wie ein Menü der obersten Visual Studio-Menüleiste hinzuzufügen.  
  
 [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Erläutert, wie eine Tastenkombination (z. B. STRG + 3) ein Menüelement hinzu.  
  
 [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)  
 Erläutert, wie im oberen Menü ein Untermenü hinzugefügt.  
  
 [Fügen Sie, dass eine zuletzt verwendete Liste aus, um ein Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Es wird erläutert, wie eine zuletzt verwendet-Liste hinzufügen.  
  
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md)  
 Beschreibt das Befehl-Elemente zu gruppieren, sodass sie in mehreren Menüs aufgenommen werden können.  
  
 [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
 Beschreibt, wie Sie einen Befehl auf eine Symbolleiste und ein Menü ein Symbol hinzu.  
  
 [Ändern Sie den Text eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
 Beschreibt die Verwendung von der `TextChanges` Kennzeichnung zum Aktivieren eines Menüelements dynamisch geändert werden.  
  
 [Ändern der Darstellung eines Befehls](../extensibility/changing-the-appearance-of-a-command.md)  
 Beschreibt, wie dynamisch aktivieren oder deaktivieren einen Befehl.  
  
 [Aktualisieren Sie die Benutzeroberfläche](../extensibility/updating-the-user-interface.md)  
 Beschreibt, wie eine Aktualisierung der Benutzeroberfläche entsprechend der zuletzt vorgenommenen Änderungen zu erzwingen.  
  
 [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)  
 Erläutert, wie zum Lokalisieren von Menübefehlen.  