---
title: Befehlsbehandlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a155927bb69c55c15a06cb058692038c8b309a30
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230868"
---
# <a name="command-handling"></a>Behandlung von Befehlen
Als Editor verwenden, kann neue Befehle definieren. Befehle werden in der Regel in einem Menü, das auf einer Symbolleiste oder in einem Kontextmenü angezeigt.  
  
 Weitere Informationen zu definieren, Befehle und Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Ein Sprachdienst kann steuern, welche Kontextmenüs im Editor angezeigt werden, durch das Abfangen der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration. Alternativ können Sie im Kontextmenü auf einer pro-Marker-Basis steuern. Weitere Informationen finden Sie unter [wichtige Befehle für den Sprachdienst Filter](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="add-commands-to-the-editor-context-menu"></a>Hinzufügen von Befehlen zu Editor-Kontextmenüs  
 Um einen Befehl im Kontextmenü hinzugefügt haben, müssen Sie zunächst eine Gruppe von Menübefehlen, die einer bestimmten Gruppe definieren. Das folgende Beispiel stammt aus dem *VSCT* Datei, die als Teil der exemplarischen Vorgehensweise generiert [Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einer benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menü-Guid = "GuidCustomEditorCmdSet" Id = "IDMX_RTF" Priorität = "0 x 0000" Type = "Kontext" >  
  
 \<Guid des übergeordneten = "GuidCustomEditorCmdSet" Id = "0" / >  
  
 \<Zeichenfolgen >  
  
 \<ButtonText > CustomEditor Kontextmenü\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Zeichenfolgen >  
  
 \</ Menü ">  
  
 \</-Menüs >  
  
 Der obige Text Fügt einen Befehl im Kontextmenü, mit dem Text **CustomEditor Kontextmenü**. Der Menü-GUID ist Teil der Befehlssatz, der mit diesem Editor erstellt wird. Der Typ ist "Kontext".  
  
 Sie können auch die vordefinierten Befehle, die nicht in definiert werden, müssen die *VSCT* Datei. Überprüfen Sie z. B. die *EditorPane.cs* Datei, die von der Visual Studio-Paket-Vorlage generiert. Sie finden, das eine Reihe von vordefinierten Befehlen, wie z. B. <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> durch definiert <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, z. B. in den Befehlshandler behandelt werden die `onSelectAll` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)