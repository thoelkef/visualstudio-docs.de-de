---
title: GUIDs und IDs der Visual Studio-Befehle | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daf131fd6d7940458252e734ab0cc222f2e3a357
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096131"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs und IDs von Visual Studio-Befehle
Die GUID und ID-Werte in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthaltenen Befehle werden in der VSCT-Dateien definiert, die als Teil der Visual Studio SDK installiert sind. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Arbeiten mit IDE-Objekten, die definiert sind *VSCT* finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Suchen Sie eine Befehlsdefinition
 Da Visual Studio mehr als 1000 Befehle definiert, ist es unpraktisch, dass sie alle hier aufgeführt. Stattdessen folgendermaßen Sie vor, um die Definition eines Befehls zu suchen.

### <a name="to-locate-a-command-definition"></a>Um eine Befehlsdefinition zu suchen.

1. In Visual Studio, öffnen Sie die folgenden Dateien in die *< Visual Studio SDK-Installationspfad\>\VisualStudioIntegration\Common\Inc\\*  Ordner: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Die meisten Visual Studio-Befehle sind in definiert *SharedCmdDef.vsct* und *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definiert Befehle, die sich an den Debugger zu beziehen und *Venusmenu.vsct* Befehle, die spezifisch für die Web-Entwicklung sind definiert.

2. Wenn der Befehl ein Menüelement ist, notieren Sie den genauen Text des Menüelements. Wenn der Befehl eine Schaltfläche auf einer Symbolleiste ist, beachten Sie den QuickInfo-Text, der angezeigt wird, wenn Sie darauf anhalten.

3. Drücken Sie **STRG**+**F** zum Öffnen der **finden** Dialogfeld.

4. In der **Suchen nach** Feld, und geben Sie in Schritt 2 den Text, die Sie notiert haben.

5. Überprüfen Sie, ob **alle geöffneten Dokumente** wird angezeigt, der **Suchen in** Feld.

6. Klicken Sie auf die **Weitersuchen** so lange, bis der Text ausgewählt ist, in der `<Strings>` Teil einer [Button-Element](../../extensibility/button-element.md).

    Die `<Button>` -Element, das in der Befehl angezeigt wird, wird der Befehlsdefinition.

   Wenn Sie die Befehlsdefinition gefunden haben, können Sie eine Kopie des Befehls in einem anderen Menü oder Symbolleiste einfügen, durch das Erstellen einer [CommandPlacement-Element](../../extensibility/commandplacement-element.md) verfügt, die über die gleiche `guid` und `id` Werte wie für den Befehl. Weitere Informationen finden Sie unter [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Sonderfälle
 In den folgenden Fällen den Menütext oder QuickInfo-Text entspricht möglicherweise nicht exakt neuerungen in der Befehlsdefinition.

- Menüelemente, die ein unterstrichenes Zeichen, z. B. enthalten die **Drucken** Befehl die **Datei** Menü, in dem die *P* unterstrichen ist.

     Zeichen, die das kaufmännische und-Zeichen vorangestellt werden (&) Zeichen in der Elementnamen im Menü angezeigt werden unterstrichen angezeigt. Allerdings *VSCT* Dateien werden geschrieben, in XML, das das kaufmännische und-Zeichen (&) verwendet, um Sonderzeichen anzugeben und erfordert, dass ein kaufmännisches und-Zeichen, die angezeigt wird, werden als geschrieben werden muss  *&amp;Amp;*. Aus diesem Grund in einer *VSCT* -Datei, die **Drucken** -Befehl angezeigt wird, als  *&amp;Amp; Drucken*.

- Befehle, die dynamischer Text, z. B. auf **speichern** \<aktuellen Dateinamen\>, und dynamisch generierte Menüelemente, z. B. die Elemente auf der **zuletzt verwendeten Dateien** Liste.

     Es ist keine zuverlässige Möglichkeit, die dynamischer Text suchen. Stattdessen finden Sie eine Gruppe, die den gewünschten Befehl von consulting hostet [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs von Visual Studio-Symbolleiste](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), und suchen Sie auf die ID dieser Gruppe. Wenn die Befehlsdefinition keinen die Gruppe als seine [übergeordnetes Element](../../extensibility/parent-element.md), Search *SharedCmdPlace.vsct* und *ShellCmdPlace.vsct* (oder  *VsDbgCmdPlace.vsct* für Debuggerbefehle) für eine `<CommandPlacement>` -Element, das das übergeordnete Element des Befehls legt diese fest. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, und *VsDbgCmdPlace.vsct* befinden sich in der *\<Visual Studio SDK-Installationspfad\>\ VisualStudioIntegration\Common\Inc\\* Ordner.

## <a name="see-also"></a>Siehe auch
- [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
