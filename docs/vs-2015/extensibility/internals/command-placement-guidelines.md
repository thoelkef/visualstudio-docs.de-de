---
title: Richtlinien zur Befehlsplatzierung Befehl | Microsoft-Dokumentation
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
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81c40e2ee18f828ad379cdaabc40854fb87ccfb8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514533"
---
# <a name="command-placement-guidelines"></a>Richtlinien zur Befehlsplatzierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Richtlinien zur Befehlsplatzierung](https://docs.microsoft.com/visualstudio/extensibility/internals/command-placement-guidelines).  
  
Bewährte Methoden für die Positionierung von Befehlen in der integrierten Entwicklungsumgebung (IDE) von Visual Studio variieren je nach Größe für den Befehlssatz. Befehle sind definiert und positioniert wird, entsprechend den Informationen in der VSCT-Dateien.  
  
## <a name="best-practices-for-all-command-sets"></a>Bewährte Methoden für alle Befehlssätze  
 Gelten Sie für jeden Satz von Befehlen folgende Richtlinien:  
  
-   Ein Diagramm mit der Befehlsstruktur im Voraus vorbereiten. Identifizieren Sie die Befehle, Kombinationsfelder, Befehlsgruppen und Kontextmenüs, die in mehreren Speicherorten verwendet werden.  
  
-   Befehle, die in der gleichen Gruppe angezeigt werden sollte verknüpft sein.  
  
-   Gruppen, die nur einen Befehl enthalten sind zulässig.  
  
-   Pakete sollten viele der Befehle nicht vorhandenen Visual Studio-Menüs hinzufügen. Stattdessen sollten sie Menüs oder Untermenüs zum Hosten der neuen Befehle erstellen.  
  
-   Wenn Sie einen Befehl auf einem vorhandenen Menü, Name, den Befehl Einfügen, damit ihr Zweck klar ist und es nicht mit vorhandenen Befehlen verwechselt werden wird.  
  
## <a name="best-practices-for-small-command-sets"></a>Bewährte Methoden für kleine Befehlssätze  
 Wenn Sie eine VSPackage, die nur wenige Befehle enthalten sind entwickeln, beachten Sie auch Folgendes:  
  
-   Verwenden Sie nach Möglichkeit die [übergeordnetes Element](../../extensibility/parent-element.md) eines Befehls, Kombinationsfeld, Gruppe oder Menü des untergeordneten, es in die entsprechende Gruppe zu platzieren.  
  
-   Weisen Sie diese Gruppen zu Menüs angezeigt, die vom VSPackage ein.  
  
-   Das übergeordnete Element eines untergeordneten Menüs oder einen Befehl muss eine [Group-Element](../../extensibility/group-element.md). Befehle und Menüs von untergeordneten Gruppen zuweisen, und klicken Sie dann die Gruppen übergeordneten Menüs zuweisen.  
  
-   Sie können einen Befehl in weiteren Gruppen einfügen, durch das Hinzufügen einer [CommandPlacements-Element](../../extensibility/commandplacements-element.md) im Abschnitt nach der Definition des Befehls, und klicken Sie dann auf Hinzufügen. die `CommandPlacements Element` eine [CommandPlacement-Element](../../extensibility/commandplacement-element.md) für jede zusätzliche Gruppe.  
  
## <a name="best-practices-for-large-command-sets"></a>Bewährte Methoden für große Befehlssätze  
 Richtlinien Sie Wenn Ihr VSPackage für viele Befehle sind, die in mehreren Kontexten angezeigt werden, auch die folgenden:  
  
-   Stellen Sie die Menüs, Gruppen und Befehle überordnen von selbst. D.h., weisen Sie keine `Parent Element` in der Definition des Elements.  
  
-   Verwendung `CommandPlacement Element` Einträge in der `CommandPlacements Element` Abschnitt, Menüs, Gruppen und Befehle in ihrer übergeordneten Menüs und Gruppen zu platzieren.  
  
-   In der `CommandPlacements` Abschnitt die Einträge, die einem bestimmten Menü Auffüllen oder die Gruppe muss neben anderen. Dies unterstützt die Lesbarkeit und macht die `Priority` Rangfolgen erheblich einfacher ermitteln.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

