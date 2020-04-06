---
title: GUIDs und IDs von Visual Studio-Befehlen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708254"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs und IDs von Visual Studio-Befehlen
Die GUID- und ID-Werte der in der integrierten Visual Studio-Entwicklungsumgebung (IDE) enthaltenen Befehle werden in .vsct-Dateien definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Arbeiten mit IDE-Objekten, die in *.vsct-Dateien* definiert sind, finden Sie unter Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Suchen einer Befehlsdefinition
 Da Visual Studio mehr als 1000 Befehle definiert, ist es nicht praktikabel, sie alle hier aufzulisten. Führen Sie stattdessen die folgenden Schritte aus, um die Definition eines Befehls zu finden.

### <a name="to-locate-a-command-definition"></a>So suchen Sie eine Befehlsdefinition

1. Öffnen Sie in Visual Studio die folgenden Dateien im *Installationspfad\><Visual\\ Studio SDK: "VisualStudioIntegration" und "Common"Inc"-Ordner:* *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Die meisten Visual Studio-Befehle sind in *SharedCmdDef.vsct* und *ShellCmdDef.vsct*definiert. *VsDbgCmdUsed.vsct* definiert Befehle, die sich auf den Debugger beziehen, und *Venusmenu.vsct* definiert Befehle, die für die Webentwicklung spezifisch sind.

2. Wenn es sich bei dem Befehl um ein Menüelement handelt, notieren Sie sich den genauen Text des Menüelements. Wenn es sich bei dem Befehl um eine Schaltfläche auf einer Symbolleiste handelt, notieren Sie sich den QuickInfo-Text, der angezeigt wird, wenn Sie ihn anhalten.

3. Drücken Sie **Strg**+**F,** um das Dialogfeld **Suchen** zu öffnen.

4. Geben Sie im Feld **Suchen, welchen** Text in Schritt 2 ein.

5. Stellen Sie sicher, dass **alle geöffneten Dokumente** im Feld **Suchen in** angezeigt werden.

6. Klicken Sie auf die Schaltfläche Weiter `<Strings>` **suchen,** bis der Text im Abschnitt eines [Schaltflächenelements](../../extensibility/button-element.md)ausgewählt ist.

    Das `<Button>` Element, in dem der Befehl angezeigt wird, ist die Befehlsdefinition.

   Wenn Sie die Befehlsdefinition gefunden haben, können Sie eine Kopie des Befehls in ein `guid` anderes `id` Menü oder eine symbolduzierter Symbolleiste setzen, indem Sie ein [CommandPlacement-Element](../../extensibility/commandplacement-element.md) erstellen, das dasselbe und die gleichen Werte wie der Befehl aufweist. Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Schaltflächengruppen](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Spezialfälle
 In den folgenden Fällen stimmt der Menütext oder QuickInfo-Text möglicherweise nicht genau mit dem in der Befehlsdefinition übereinstimmt.

- Menüelemente, die ein unterstrichenes Zeichen enthalten, z. B. den Befehl **Drucken** im Menü **Datei,** in dem das *P* unterstrichen ist.

     Zeichen, denen das &-Zeichen (&) in Menüelementnamen vorangestellt ist, werden als unterstrichen angezeigt. *.vsct-Dateien* werden jedoch in XML geschrieben, das das zeichen sandsand (&) verwendet, um Sonderzeichen anzugeben, und erfordert, dass ein und ein spersand angezeigt werden muss, muss als * &amp;amp;* geschrieben werden. Daher wird in einer *.vsct-Datei* der **Befehl Drucken** als * &amp;Amp; Drucken*.

- Befehle mit dynamischem Text, z.\>B. Aktuelle Dateinamen **speichern** \<und dynamisch generierte Menüelemente, z. B. die Elemente in der Liste **"Letzte Dateien".**

     Es gibt keine zuverlässige Möglichkeit, nach dynamischem Text zu suchen. Suchen Sie stattdessen eine Gruppe, die den gewünschten Befehl hostet, indem Sie [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)konsultieren, und suchen Sie nach der ID dieser Gruppe. Wenn die Befehlsdefinition nicht über die Gruppe als [übergeordnetes Element](../../extensibility/parent-element.md)verfügt, suchen Sie *SharedCmdPlace.vsct* und *ShellCmdPlace.vsct* `<CommandPlacement>` (oder *VsDbgCmdPlace.vsct* für Debuggerbefehle) nach einem Element, das das übergeordnete Element des Befehls festlegt. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*und *VsDbgCmdPlace.vsct* befinden sich im * \<Visual Studio SDK-Installationspfad .\>\\ *

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
