---
title: Standardbefehl, Gruppen- und Symbolleistenplatzierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708889"
---
# <a name="default-command-group-and-toolbar-placement"></a>Standardbefehls-, Gruppen- und Symbolleistenplatzierung
Für Produktgleichmäßigkeit und -stabilität zeigt die Benutzeroberfläche [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] standardmäßig bestimmte Befehlsgruppen an und stellt Definitionen für Befehle und Befehlsgruppen bereit. VSPackages kann auch die Standardbefehle und Befehlsgruppen verwenden.

 Die Standardbefehlsgruppen lassen sich in drei Kategorien einteilen: IDE-Befehle, Produktbefehle und Editorbefehle.

## <a name="default-ide-commands"></a>Standard-IDE-Befehle
 Die Standardsymbolleiste IDE enthält Befehle, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]die von allen in enthaltenen Produkten gemeinsam verwendet werden. Dazu gehören Befehle, die sich auf generische Projektoperationen beziehen, z. B. den Befehl **Speichern** und den Befehl **Element hinzufügen.** VSPackages sollte dieser Symbolleiste nicht hinzugefügt oder von ihnen subtrahiert werden, mit einer Ausnahme: Wenn das Produkt oder VSPackage ein neues Toolfenster hinzufügt, sollte das Fenster der Liste der verfügbaren Toolfenster im Menü **Ansicht** hinzugefügt werden. Neue Produkte oder VSPackages können ihre eigene Symbolleiste hinzufügen.

## <a name="default-product-commands"></a>Standardproduktbefehle
 Jedes Produkt kann der IDE eine eigene Standardsymbolleiste bereitstellen, die wichtige und häufig verwendete Befehle enthält. Es ist jedoch am besten, vorhandene Menüs und Symbolleisten zu verwenden, wann immer möglich, und sie bei Bedarf mit anderen aufgabenspezifischen Symbolleisten zu ergänzen.

 Das Prioritätsfeld für eine Symbolleiste bestimmt die Zeilenplatzierung. Nullpriorität platziert die Symbolleiste in der dritten Zeile (Zeile 3), unter der Menüleiste (Zeile 1) und der **Standardsymbolleiste** (Zeile 2). Daher werden andere Symbolleisten in der Zeile angezeigt (Priorität + 3). Nachfolgende Symbolleisten werden auf derselben Zeile platziert, wenn Platz vorhanden ist. Andernfalls werden sie automatisch in die nächste Zeile verschoben.

## <a name="default-editor-commands"></a>Standard-Editor-Befehle
 Ein VSPackage, das einen benutzerdefinierten Editor bereitstellt, sollte eine Standardsymbolleiste bereitstellen, die die wichtigsten und am häufigsten verwendeten Befehle in diesem Editor enthält. Die Editor-Symbolleiste sollte angezeigt werden, wenn der Editor aktiv ist, und ausgeblendet werden, wenn der Editor nicht aktiv ist. Diese Sichtbarkeit wird `VisibilityConstraints` im Element der *.vsct-Datei* gesteuert.

 Editor-Symbolleisten sollten unter IDE- und Produktsymbolleisten platziert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
