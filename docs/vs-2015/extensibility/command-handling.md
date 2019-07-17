---
title: Befehlsbehandlung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184376"
---
# <a name="command-handling"></a>Verarbeiten von Befehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Als Editor verwenden, kann neue Befehle definieren. Befehle werden in der Regel in einem Menü, das auf einer Symbolleiste oder in einem Kontextmenü angezeigt.  
  
 Weitere Informationen zu definieren, Befehle und Menüs, finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Ein Sprachdienst kann steuern, welche Kontextmenüs im Editor angezeigt werden, durch das Abfangen der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration. Alternativ können Sie im Kontextmenü auf einer pro-Marker-Basis steuern. Weitere Informationen finden Sie unter [wichtige Befehle für Sprachdienstfilter](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Hinzufügen von Befehlen zu Editor-Kontextmenüs  
 Um einen Befehl im Kontextmenü hinzugefügt haben, müssen Sie zunächst eine Gruppe von Menübefehlen, die einer bestimmten Gruppe definieren. Das folgende Beispiel stammt aus der VSCT-Datei, die als Teil der exemplarischen Vorgehensweise generiert [Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Zeichenfolgen >  
  
 \<ButtonText > CustomEditor Kontextmenü\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Zeichenfolgen >  
  
 \</ Menü ">  
  
 \</-Menüs >  
  
 Der obige Text Fügt einen Befehl im Kontextmenü, mit dem Text **CustomEditor Kontextmenü**. Die Menü-GUID ist, dass für den Befehlssatz, mit diesem Editor erstellt wird, und der Typ ist "Kontext".  
  
 Sie können auch die vordefinierten Befehle verwenden, die nicht in der VSCT-Datei definiert werden müssen. Z. B. Wenn Sie die EditorPane.cs-Datei, die von der Visual Studio-Paket-Vorlage generiert untersuchen, finden Sie, die eine Reihe von vordefinierten Befehlen, wie z. B. <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> von definierten <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, in den Befehlshandler, z. B. die OnSelectAll-Methode behandelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
