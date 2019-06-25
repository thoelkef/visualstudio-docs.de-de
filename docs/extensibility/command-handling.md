---
title: Befehlsbehandlung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52c47e7dca715859408f1697fd31f1a1a2cf534b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315549"
---
# <a name="command-handling"></a>Behandlung von Befehlen
Als Editor verwenden, kann neue Befehle definieren. Befehle werden in der Regel in einem Menü, das auf einer Symbolleiste oder in einem Kontextmenü angezeigt.

 Weitere Informationen zu definieren, Befehle und Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

 Ein Sprachdienst kann steuern, welche Kontextmenüs im Editor angezeigt werden, durch das Abfangen der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration. Alternativ können Sie im Kontextmenü auf einer pro-Marker-Basis steuern. Weitere Informationen finden Sie unter [wichtige Befehle für den Sprachdienst Filter](../extensibility/internals/important-commands-for-language-service-filters.md).

## <a name="add-commands-to-the-editor-context-menu"></a>Hinzufügen von Befehlen zu Editor-Kontextmenüs
 Um einen Befehl im Kontextmenü hinzugefügt haben, müssen Sie zunächst eine Gruppe von Menübefehlen, die einer bestimmten Gruppe definieren. Das folgende Beispiel stammt aus dem *VSCT* Datei, die als Teil der exemplarischen Vorgehensweise generiert [Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einer benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):

 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">

 \<Parent guid="guidCustomEditorCmdSet" id="0"/>

 \<Strings>

 \<ButtonText > CustomEditor Kontextmenü\</ButtonText >

 \<CommandName>CustomEditorContextMenu\</CommandName>

 \</Strings>

 \</ Menü ">

 \</Menus>

 Der obige Text Fügt einen Befehl im Kontextmenü, mit dem Text **CustomEditor Kontextmenü**. Der Menü-GUID ist Teil der Befehlssatz, der mit diesem Editor erstellt wird. Der Typ ist "Kontext".

 Sie können auch die vordefinierten Befehle, die nicht in definiert werden, müssen die *VSCT* Datei. Überprüfen Sie z. B. die *EditorPane.cs* Datei, die von der Visual Studio-Paket-Vorlage generiert. Sie finden, das eine Reihe von vordefinierten Befehlen, wie z. B. <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> durch definiert <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, z. B. in den Befehlshandler behandelt werden die `onSelectAll` Methode.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)