---
title: Richtlinien zur Platzierung Befehl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e74bda24459bedeef007b451c7fabe3922e7ab37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="command-placement-guidelines"></a>Richtlinien zur Platzierung Befehl
Bewährte Methoden für die Positionierung von Befehlen in der integrierten Entwicklungsumgebung (IDE) von Visual Studio variieren je nach Größe für den Befehlssatz. Befehle sind definiert, und je nach den Informationen in der VSCT-Dateien eingerückt.  
  
## <a name="best-practices-for-all-command-sets"></a>Bewährte Methoden für alle Befehlssätze  
 Gelten Sie für jeden Satz von Befehlen folgende Richtlinien:  
  
-   Bereiten Sie ein Diagramm mit der Befehlsstruktur im voraus. Identifizieren Sie die Befehle, Kombinationsfelder, Befehlsgruppen und Kontextmenüs, die mehr als einer Stelle verwendet werden.  
  
-   Befehle, die in der gleichen Gruppe angezeigt werden sollte verknüpft werden.  
  
-   Gruppen, die nur ein Befehl enthalten, sind gültig.  
  
-   Pakete sollten nicht viele Befehle zu vorhandenen Visual Studio-Menüs hinzufügen. Stattdessen sollten sie Menüs oder Untermenüs zum Hosten der neuen Befehle erstellen.  
  
-   Wenn Sie einen Befehl auf einem vorhandenen Menü, Name des Befehls erstellen, damit dessen Zweck eindeutig ist und nicht mit vorhandenen Befehlen verwechselt werden wird.  
  
## <a name="best-practices-for-small-command-sets"></a>Bewährte Methoden für kleine Befehlssätze  
 Wenn Sie eine VSPackage, die nur wenige Befehle enthalten sind entwickeln, gelten Sie auch folgende Richtlinien:  
  
-   Verwenden Sie nach Möglichkeit die [übergeordneten Elements](../../extensibility/parent-element.md) eines Befehls, Kombinationsfeld, Gruppe oder untergeordneten im Menü, in die entsprechende Gruppe eingefügt werden soll.  
  
-   Weisen Sie diese Gruppen zu Menüs angezeigt werden, von dem VSPackage.  
  
-   Das übergeordnete Element eines untergeordneten Menüs oder eines Befehls muss ein [Gruppenelement](../../extensibility/group-element.md). Zuweisen von Befehlen und untergeordnete Menüs zu Gruppen, und weisen Sie die Gruppen mit übergeordneten Menüs.  
  
-   Sie können zusätzliche Gruppen hinzufügen ein Befehls gelagerte eine [CommandPlacements Element](../../extensibility/commandplacements-element.md) nach der Definition des Befehls Abschnitt, und klicken Sie dann zum Hinzufügen der `CommandPlacements Element` eine [CommandPlacement-Element](../../extensibility/commandplacement-element.md) für jede zusätzliche Gruppe.  
  
## <a name="best-practices-for-large-command-sets"></a>Best Practices für große Befehlssätze  
 Wenn Ihr VSPackage viele Befehle verfügt, die in mehreren Kontexten angezeigt werden, gelten Sie auch folgende Richtlinien:  
  
-   Stellen Sie die Menüs, Gruppen und Befehle, die Self-Überordnung. Weisen Sie also keiner `Parent Element` in der Definition des Elements.  
  
-   Verwendung `CommandPlacement Element` Einträge in der `CommandPlacements Element` Abschnitt, Menüs, Gruppen und Befehle aus, die in den übergeordneten Menüs und Gruppen eingefügt werden soll.  
  
-   In der `CommandPlacements` Abschnitt, der Einträge, die einem bestimmten Menü Auffüllen oder Gruppe aneinander angrenzenden sein sollte. Dies erleichtert die Lesbarkeit und macht die `Priority` Rangfolgen erheblich einfacher ermitteln.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)