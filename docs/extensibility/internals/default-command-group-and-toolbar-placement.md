---
title: Standard-Befehl, Gruppe und Symbolleiste Platzierung | Microsoft-Dokumentation
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e84ca70383facc608740cd42a29c4ee769adb069
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609669"
---
# <a name="default-command-group-and-toolbar-placement"></a>Standardplatzierung-Befehl, Gruppe und Symbolleiste
Für Produkt Einheitlichkeit und Stabilität, die Benutzeroberfläche zeigt die bestimmte Befehlsgruppen und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthält Definitionen für Befehle und Befehlsgruppen. VSPackages können sich auch auf die Standardbefehle und Befehlsgruppen aus.

 Die Standard-Befehlsgruppen fallen in drei Kategorien: IDE-Befehle, Produkt und -Editor-Befehlen.

## <a name="default-ide-commands"></a>Standard-IDE-Befehle
 Die Standard-IDE-Symbolleiste enthält Befehle, die von allen Produkten, die in enthaltenen freigegebene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Hierzu gehören auch Befehle, die im Zusammenhang mit generischen Projektvorgänge, z. B. die **speichern** Befehl und die **Element hinzufügen** Befehl. VSPackages, die nicht hinzugefügt oder subtrahiert dieser Symbolleiste, mit einer Ausnahme: Wenn das Produkt oder die VSPackage-ein neues Toolfenster fügt, das Fenster zur Liste der verfügbaren Toolfenstern hinzugefügt werden sollen, auf die **Ansicht** Menü. Neue Produkte oder VSPackages können eine eigene Symbolleiste hinzufügen.

## <a name="default-product-commands"></a>Standardbefehle-Produkt
 Jedes Produkt kann es sich um die IDE mit eigenen Standardsymbolleiste bereitstellen, enthält wichtige und häufig verwendete Befehle. Es wird jedoch empfohlen, verwenden Sie vorhandenen Menüs und Symbolleisten, wann immer möglich und ergänzen diese anderen aufgabenspezifische Symbolleisten je nach Bedarf.

 Das Feld "Priorität" für eine Symbolleiste bestimmt die Platzierung der Zeile. 0 (null) Priorität die Symbolleiste auf die dritte Zeile (Zeile 3), unter der Menüleiste platziert (Zeile 1) und die **Standard** Symbolleiste (Zeile 2). Aus diesem Grund anderen Symbolleisten angezeigt werden, in Zeile ("Priorität" + "3"). Nachfolgende Symbolleisten werden auf der gleichen Zeile platziert, wenn genügend Platz vorhanden ist; Andernfalls werden sie automatisch in die nächste Zeile verschoben.

## <a name="default-editor-commands"></a>Standard-Editor-Befehlen
 Eine VSPackage, die einen benutzerdefinierten Editor enthält, sollten eine Standardsymbolleiste bereitstellen, die enthält die wichtigsten und häufig verwendete Befehle in Editor. Die Editor-Symbolleiste sollte angezeigt werden, wenn der Editor aktiv ist und ausgeblendet werden soll, wenn der Editor nicht aktiv ist. Diese Sichtbarkeit wird gesteuert, der `VisibilityConstraints` Element der *VSCT* Datei.

 Editor-Symbolleisten sollten unter IDE und Produkt Symbolleisten platziert werden.

## <a name="see-also"></a>Siehe auch
- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)