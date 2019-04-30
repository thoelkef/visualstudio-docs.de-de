---
title: Richtlinien zur Befehlsplatzierung Befehl | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c04ea981fc190b2e0074e767e086303e6950f2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861658"
---
# <a name="command-placement-guidelines"></a>Richtlinien zur befehlsplatzierung
Bewährte Methoden für die Positionierung von Befehlen in der integrierten Entwicklungsumgebung (IDE) von Visual Studio variieren je nach Größe für den Befehlssatz. Befehle definiert sind, und entsprechend den Informationen in positioniert *VSCT* Dateien.

## <a name="best-practices-for-all-command-sets"></a>Bewährte Methoden für alle Befehlssätze
 Gelten Sie für jeden Satz von Befehlen folgende Richtlinien:

- Ein Diagramm mit der Befehlsstruktur im Voraus vorbereiten. Identifizieren Sie die Befehle, Kombinationsfelder, Befehlsgruppen und Kontextmenüs, die in mehreren Speicherorten verwendet werden.

- Befehle, die in der gleichen Gruppe angezeigt werden sollte verknüpft sein.

- Gruppen, die nur einen Befehl enthalten sind zulässig.

- Pakete sollten viele der Befehle nicht vorhandenen Visual Studio-Menüs hinzufügen. Stattdessen sollten sie Menüs oder Untermenüs zum Hosten der neuen Befehle erstellen.

- Wenn Sie einen Befehl auf einem vorhandenen Menü, Name, den Befehl Einfügen, damit ihr Zweck klar ist und es nicht mit vorhandenen Befehlen verwechselt werden wird.

## <a name="best-practices-for-small-command-sets"></a>Bewährte Methoden für kleine Befehlssätze
 Wenn Sie eine VSPackage, die nur wenige Befehle enthalten sind entwickeln, beachten Sie auch Folgendes:

- Verwenden Sie nach Möglichkeit die [übergeordneten](../../extensibility/parent-element.md) Element ein, Kombinationsfeld, Gruppe oder eines untergeordneten Menüs, es in die entsprechende Gruppe zu platzieren.

- Weisen Sie diese Gruppen zu Menüs angezeigt, die vom VSPackage ein.

- Das übergeordnete Element eines untergeordneten Menüs oder einen Befehl muss eine [Gruppe](../../extensibility/group-element.md) Element. Befehle und Menüs von untergeordneten Gruppen zuweisen, und klicken Sie dann die Gruppen übergeordneten Menüs zuweisen.

- Sie können einen Befehl in weiteren Gruppen einfügen, durch das Hinzufügen einer [CommandPlacements](../../extensibility/commandplacements-element.md) -Elementabschnitt nach der Definition des Befehls, und klicken Sie dann zum Hinzufügen der `CommandPlacements` Element eine [CommandPlacement](../../extensibility/commandplacement-element.md) Element für jede weitere Gruppe.

## <a name="best-practices-for-large-command-sets"></a>Bewährte Methoden für große Befehlssätze
 Richtlinien Sie Wenn Ihr VSPackage für viele Befehle sind, die in mehreren Kontexten angezeigt werden, auch die folgenden:

- Stellen Sie die Menüs, Gruppen und Befehle überordnen von selbst. D.h., weisen Sie keine `Parent` Element in der Definition des Elements.

- Verwendung `CommandPlacement` Element Einträge in der `CommandPlacements` -Elementabschnitt, Menüs, Gruppen und Befehle in ihrer übergeordneten Menüs und Gruppen zu platzieren.

- In der `CommandPlacements` werden im Elementabschnitt, der Einträge, die Werte eines beliebigen Menüs oder einer Gruppe nebeneinander an. Dies unterstützt die Lesbarkeit und macht die `Priority` Rangfolgen erheblich einfacher ermitteln.

## <a name="see-also"></a>Siehe auch
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)