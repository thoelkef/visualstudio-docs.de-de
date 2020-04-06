---
title: Richtlinien für die Befehlsplatzierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709569"
---
# <a name="command-placement-guidelines"></a>Richtlinien für die Befehlsplatzierung
Bewährte Methoden für das Positionieren von Befehlen in der integrierten Visual Studio-Entwicklungsumgebung (IDE) hängen von der Größe des Befehlssatzes ab. Befehle werden entsprechend den Informationen in *.vsct-Dateien* definiert und positioniert.

## <a name="best-practices-for-all-command-sets"></a>Bewährte Methoden für alle Befehlssätze
 Befolgen Sie für jeden Befehlssatz die folgenden Richtlinien:

- Bereiten Sie ein Diagramm der Befehlsstruktur im Voraus vor. Identifizieren Sie die Befehle, Kombinationsfelder, Befehlsgruppen und Kontextmenüs, die an mehr als einer Position verwendet werden.

- Befehle, die in derselben Gruppe angezeigt werden, sollten miteinander verknüpft sein.

- Gruppen, die nur einen Befehl enthalten, sind akzeptabel.

- Pakete sollten nicht viele Befehle zu vorhandenen Visual Studio-Menüs hinzufügen. Stattdessen sollten sie Menüs oder Untermenüs erstellen, um die neuen Befehle zu hosten.

- Wenn Sie einen Befehl in einem vorhandenen Menü eingeben, benennen Sie den Befehl so, dass sein Zweck klar ist und er nicht mit vorhandenen Befehlen verwechselt wird.

## <a name="best-practices-for-small-command-sets"></a>Bewährte Methoden für kleine Befehlssätze
 Wenn Sie ein VSPackage mit nur wenigen Befehlen entwickeln, befolgen Sie auch die folgenden Richtlinien:

- Verwenden Sie nach Möglichkeit das [übergeordnete](../../extensibility/parent-element.md) Element eines Befehls,Kombifelds, einer Gruppe oder eines untergeordneten Menüs, um es in die entsprechende Gruppe einzuteilen.

- Weisen Sie diese Gruppen Menüs zu, die vom VSPackage angezeigt werden.

- Das übergeordnete Element eines untergeordneten Menüs oder eines Befehls muss ein [Group-Element](../../extensibility/group-element.md) sein. Weisen Sie Gruppen Befehle und untergeordnete Menüs zu, und weisen Sie die Gruppen dann übergeordneten Menüs zu.

- Sie können einen Befehl in zusätzliche Gruppen eingeben, indem Sie nach der Definition des `CommandPlacements` Befehls einen [CommandPlacements-Elementabschnitt](../../extensibility/commandplacements-element.md) hinzufügen und dem Element dann ein [CommandPlacement-Element](../../extensibility/commandplacement-element.md) für jede weitere Gruppe hinzufügen.

## <a name="best-practices-for-large-command-sets"></a>Bewährte Methoden für große Befehlssätze
 Wenn Ihr VSPackage über viele Befehle verfügt, die in mehreren Kontexten angezeigt werden, befolgen Sie auch die folgenden Richtlinien:

- Erstellen Sie Menüs, Gruppen und Befehle zur Selbsterziehung. Das heißt, weisen `Parent` Sie kein Element in der Definition des Elements zu.

- Verwenden `CommandPlacement` Sie Elementeinträge im `CommandPlacements` Elementabschnitt, um Menüs, Gruppen und Befehle in die übergeordneten Menüs und Gruppen einzuteilen.

- Im `CommandPlacements` Elementabschnitt sollten die Einträge, die ein bestimmtes Menü oder eine bestimmte Gruppe auffüllen, nebeneinander liegen. Dies erleichtert die `Priority` Lesbarkeit und erleichtert die Ermittlung der Rankings.

## <a name="see-also"></a>Weitere Informationen
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
