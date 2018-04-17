---
title: Befehlsbehandlung | Microsoft Docs
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
ms.openlocfilehash: 542277c5d8ab1b9b130f31bbb06215d8da7bc2ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="command-handling"></a>Befehlsbehandlung
Der Editor kann neue Befehle definieren. Befehle werden in der Regel in einem Menü, das auf einer Symbolleiste oder in einem Kontextmenü angezeigt.  
  
 Weitere Informationen zum Definieren von Befehlen und Menüs finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Ein Sprachdienst kann steuern, welche Kontextmenüs im Editor angezeigt werden, durch Abfangen der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration. Alternativ können Sie im Kontextmenü auf Basis eines pro-Marker steuern. Weitere Informationen finden Sie unter [wichtige Befehle für Language Service Filter](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Hinzufügen von Befehlen zu Editor-Kontextmenüs  
 Um einen Befehl im Kontextmenü den Befehl hinzuzufügen, müssen Sie zunächst einen Satz von Menübefehlen, die zu einer bestimmten Gruppe gehören definieren. Das folgende Beispiel stammt aus der VSCT-Datei, die als Teil der exemplarischen Vorgehensweise generiert [Exemplarische Vorgehensweise: Hinzufügen von Funktionen eines benutzerdefinierten Editors](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menü-Guid = "GuidCustomEditorCmdSet" Id = "IDMX_RTF" Priorität = "0 x 0000" Type = "Context" >  
  
 \<Übergeordnete Guid = "GuidCustomEditorCmdSet" Id = "0" / >  
  
 \<Zeichenfolgen >  
  
 \<ButtonText > CustomEditor Kontextmenü\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Zeichenfolgen, die >  
  
 \</ Menü >  
  
 \</-Menüs >  
  
 Die oben genannten Text Fügt einen Befehl im Kontextmenü, mit dem Text **CustomEditor Kontextmenü**. Die im Menü-GUID ist, dass für den Befehlssatz, mit diesem Editor erstellt wird, und der Typ ist "Kontext".  
  
 Sie können auch die vordefinierten Befehle verwenden, die nicht in der VSCT-Datei definiert werden müssen. Z. B. Wenn Sie von der Visual Studio-Paketvorlage generierte EditorPane.cs Datei untersuchen, finden Sie, die eine Reihe von vordefinierten Befehlen, wie z. B. <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> durch definierten <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, in der Befehlshandler z. B. die Methode OnSelectAll behandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)