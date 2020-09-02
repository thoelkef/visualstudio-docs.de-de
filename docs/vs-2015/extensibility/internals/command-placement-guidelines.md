---
title: Richtlinien für die Befehls Platzierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d88a477403c98ff11c5f7303b55f5eb713b668c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195104"
---
# <a name="command-placement-guidelines"></a>Richtlinien zur Befehlsplatzierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die bewährten Methoden zum Positionieren von Befehlen in der integrierten Entwicklungsumgebung (IDE) von Visual Studio variieren in Abhängigkeit von der Größe des Befehlssatzes. Befehle werden gemäß den Informationen in vsct-Dateien definiert und positioniert.  
  
## <a name="best-practices-for-all-command-sets"></a>Bewährte Methoden für alle Befehls Sätze  
 Befolgen Sie für jeden Satz von Befehlen die folgenden Richtlinien:  
  
- Bereiten Sie ein Diagramm der Befehlsstruktur vorab vor. Identifizieren Sie die Befehle, Kombinations Felder, Befehls Gruppen und Kontextmenüs, die an mehr als einem Ort verwendet werden.  
  
- Befehle, die in derselben Gruppe angezeigt werden, sollten verknüpft sein.  
  
- Gruppen, die nur einen Befehl enthalten, sind zulässig.  
  
- Pakete sollten vorhandenen Visual Studio-Menüs nicht viele Befehle hinzufügen. Stattdessen sollten Sie Menüs oder Untermenüs erstellen, um die neuen Befehle zu hosten.  
  
- Wenn Sie einen Befehl in ein vorhandenes Menü Einfügen, benennen Sie den Befehl so, dass der Zweck eindeutig ist und nicht mit vorhandenen Befehlen verwechselt wird.  
  
## <a name="best-practices-for-small-command-sets"></a>Bewährte Methoden für kleine Befehls Sätze  
 Wenn Sie ein VSPackage entwickeln, das nur einige wenige Befehle enthält, beachten Sie auch die folgenden Richtlinien:  
  
- Verwenden Sie nach Möglichkeit das über [geordnete Element](../../extensibility/parent-element.md) eines Befehls, eines Kombinations Felds, einer Gruppe oder eines untergeordneten Menüs, um es in die entsprechende Gruppe einzufügen.  
  
- Weisen Sie diese Gruppen den Menüs zu, die durch das VSPackage angezeigt werden.  
  
- Das übergeordnete Element eines untergeordneten Menüs oder eines Befehls muss ein [Group-Element](../../extensibility/group-element.md)sein. Weisen Sie den Gruppen Befehle und untergeordnete Menüs zu, und weisen Sie die Gruppen dann den übergeordneten Menüs zu.  
  
- Sie können einen Befehl in weitere Gruppen einfügen, indem Sie nach der Definition des Befehls einen Abschnitt [commandplacement-Element](../../extensibility/commandplacements-element.md) hinzufügen und dann dem `CommandPlacements Element` [Element commandplacement](../../extensibility/commandplacement-element.md) für jede weitere Gruppe hinzufügen.  
  
## <a name="best-practices-for-large-command-sets"></a>Bewährte Methoden für große Befehls Sätze  
 Wenn das VSPackage viele Befehle enthält, die in mehreren Kontexten angezeigt werden, beachten Sie auch die folgenden Richtlinien:  
  
- Ändern Sie die selbst Verarbeitung von Menüs, Gruppen und Befehlen. Das heißt, Sie weisen keinen `Parent Element` in der Definition des Elements zu.  
  
- Verwenden `CommandPlacement Element` Sie Einträge im `CommandPlacements Element` Abschnitt, um Menüs, Gruppen und Befehle in ihren übergeordneten Menüs und Gruppen zu platzieren.  
  
- Im `CommandPlacements` Abschnitt müssen die Einträge, die ein bestimmtes Menü oder eine bestimmte Gruppe auffüllen, nebeneinander angeordnet werden. Dies unterstützt die Lesbarkeit und erleichtert die `Priority` Bestimmung der Rangfolgen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
