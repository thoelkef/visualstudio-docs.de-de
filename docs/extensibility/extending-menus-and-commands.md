---
title: Erweitern von Menüs und Befehlen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711800"
---
# <a name="extend-menus-and-commands"></a>Erweitern von Menüs und Befehlen
Befehle sind die Art und Weise, wie Sie Visual Studio Aktionen und Prozesse hinzufügen. In den meisten Fällen werden Befehle in Menüs oder Symbolleisten angezeigt. Die VSPackage-Projektvorlage zeigt, wie ein sehr einfacher Befehl implementiert wird. Für eine etwas längere, aber immer noch grundlegende Implementierung finden Sie weitere Informationen unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

 Weitere Informationen zu Visual Studio-Befehlen, Menüs und Symbolleisten finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

 Befehle, Menüs und Symbolleisten werden in der *.vsct-Datei* definiert, die Teil von VSPackage-Projekten ist. Informationen zur Visual Studio-IDE und zur *.vsct-Datei* finden Sie unter Hinzufügen von [Benutzeroberflächenelementen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)durch VSPackages .

 In den folgenden Themen wird erläutert, wie Verschiedene Arten von Befehlen, Menüs und Symbolleisten hinzugefügt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Erläutert das Hinzufügen eines Menüs zur oberen Visual Studio-Menüleiste.

- [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Erläutert das Hinzufügen einer Tastenkombination (z. B. STRG + 3) zu einem Menüelement.

- [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md) Erläutert, wie dem oberen Menü ein Untermenü hinzugefügt wird.

- [Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Erläutert das Hinzufügen einer Liste der zuletzt verwendeten Personen.

- [Erstellen wiederverwendbarer Schaltflächengruppen](../extensibility/creating-reusable-groups-of-buttons.md) Beschreibt, wie Befehlselemente gruppiert werden, damit sie in mehreren Menüs enthalten sein können.

- [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md) Beschreibt das Hinzufügen eines Symbols zu einem Befehl sowohl auf einer Symbolleiste als auch in einem Menü.

- [Ändern des Textes eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) Beschreibt die Verwendung `TextChanges` des Flags, um eine dynamische Änderung eines Menüelements zu ermöglichen.

- [Ändern der Darstellung eines Befehls](../extensibility/changing-the-appearance-of-a-command.md) Beschreibt, wie ein Befehl dynamisch aktiviert oder deaktiviert wird.

- [Aktualisieren der Benutzeroberfläche](../extensibility/updating-the-user-interface.md) Beschreibt, wie eine Aktualisierung der Benutzeroberfläche erzwingt wird, um die letzten Änderungen widerzuspiegeln.

- [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Erläutert, wie Menübefehle lokalisiert werden.
