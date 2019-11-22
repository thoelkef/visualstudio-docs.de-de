---
title: GUIDs und IDs von Visual Studio-Befehlen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186632"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs und IDs von Visual Studio-Befehlen
Die GUID-und ID-Werte der Befehle, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten sind, werden in vsct-Dateien definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Arbeiten mit IDE-Objekten, die in *vsct* -Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Suchen einer Befehls Definition
 Da Visual Studio mehr als 1000 Befehle definiert, ist es unpraktisch, Sie hier aufzulisten. Führen Sie stattdessen die folgenden Schritte aus, um die Definition eines Befehls zu suchen.

### <a name="to-locate-a-command-definition"></a>So suchen Sie eine Befehls Definition

1. Öffnen Sie in Visual Studio die folgenden Dateien im *< Visual Studio SDK-Installationspfad\>\visualstudiointegration\common\inc\\* Ordner: *sharedcmddef. vsct*, *shellcmddef. vsct*, *vsdbgcmdused. vsct*, *Venupmenu. vsct*.

    Die meisten Visual Studio-Befehle sind in " *sharedcmddef. vsct* " und " *shellcmddef. vsct*" definiert. *Vsdbgcmdused. vsct* definiert Befehle, die den Debugger betreffen, und *venlaufmenu. vsct* definiert Befehle, die für die Webentwicklung spezifisch sind.

2. Wenn es sich bei dem Befehl um ein Menü Element handelt, notieren Sie den genauen Text des Menü Elements. Wenn der Befehl eine Schaltfläche auf einer Symbolleiste ist, notieren Sie sich den QuickInfo-Text, der angezeigt wird, wenn Sie ihn anhalten.

3. Drücken Sie **STRG**+**F** , um das Dialogfeld **Suchen** zu öffnen.

4. Geben Sie im Feld **Suchen** nach den Text ein, den Sie in Schritt 2 notiert haben.

5. Vergewissern Sie sich, dass **alle geöffneten Dokumente** im Feld **Suchen in** angezeigt werden.

6. Klicken Sie auf die Schaltfläche **weiter suchen** , bis der Text im `<Strings>` Abschnitt eines [Schaltflächen Elements](../../extensibility/button-element.md)ausgewählt ist.

    Das `<Button>` Element, in dem der Befehl angezeigt wird, ist die Befehls Definition.

   Wenn Sie die Befehls Definition gefunden haben, können Sie eine Kopie des Befehls in ein anderes Menü oder eine Symbolleiste einfügen, indem Sie ein [commandplacement-Element](../../extensibility/commandplacement-element.md) erstellen, das die gleichen `guid` und `id` Werte wie der Befehl hat. Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Gruppen von Schalt](../../extensibility/creating-reusable-groups-of-buttons.md)Flächen.

### <a name="special-cases"></a>Sonderfälle
 In den folgenden Fällen stimmt der TextText oder der QuickInfo-Text möglicherweise nicht genau mit dem in der Befehls Definition überein.

- Menü Elemente, die ein unterstrichenes Zeichen enthalten, wie z. b. den Befehl " **Drucken** " im Menü " **Datei** ", in dem *P* unterstrichen ist.

     Zeichen, denen das kaufmännische und-Zeichen (&) in den Menü Elementnamen vorangestellt werden, werden als unterstrichen angezeigt. *Vsct* -Dateien werden jedoch in XML geschrieben, wobei das kaufmännische und-Zeichen (&) verwendet werden, um Sonderzeichen anzugeben. Außerdem muss ein kaufmännisches und-Zeichen als *&amp;amp;* ausgeschrieben werden. Daher wird in einer *vsct* -Datei der Befehl **Drucken** als *&amp;amp; Drucken*.

- Befehle mit dynamischem Text, z. b. **Speichern** \<aktuellen Dateinamen\>und dynamisch generierte Menü Elemente, wie z. b. die Elemente in der Liste **zuletzt verwendete Dateien** .

     Es gibt keine zuverlässige Möglichkeit, nach dynamischem Text zu suchen. Suchen Sie stattdessen eine Gruppe, die den gewünschten Befehl hostet, indem Sie [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)verwenden und nach der ID dieser Gruppe suchen. Wenn die Befehls Definition nicht die Gruppe als über [geordnetes Element](../../extensibility/parent-element.md)hat, suchen Sie *sharedcmdplace. vsct* und *shellcmdplace. vsct* (oder *vsdbgcmdplace. vsct* für Debugger-Befehle) für ein `<CommandPlacement>` Element, das das übergeordnete Element des s. " *Sharedcmdplace. vsct*", " *shellcmdplace. vsct*" und " *vsdbgcmdplace. vsct* " befinden sich im *\<Visual Studio SDK-Installationspfad\>\visualstudiointegration\common\inc\\* Ordner.

## <a name="see-also"></a>Siehe auch

- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md)
