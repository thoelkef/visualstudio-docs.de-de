---
title: Befehls Behandlung | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184376"
---
# <a name="command-handling"></a>Verarbeiten von Befehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Editor kann neue Befehle definieren. Befehle werden in der Regel in einem Menü, auf einer Symbolleiste oder in einem Kontextmenü angezeigt.  
  
 Weitere Informationen zum Definieren von Befehlen und Menüs finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Ein Sprachdienst kann steuern, welche Kontextmenüs im Editor angezeigt werden, indem die- <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration abgefangen wird. Alternativ können Sie das Kontextmenü auf der Grundlage eines Markers steuern. Weitere Informationen finden Sie unter [wichtige Befehle für Sprachdienst Filter](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Hinzufügen von Befehlen zum Editor-Kontextmenü  
 Um dem Kontextmenü einen Befehl hinzuzufügen, müssen Sie zunächst einen Satz von Menübefehlen definieren, die zu einer bestimmten Gruppe gehören. Das folgende Beispiel stammt aus der vsct-Datei, die im Rahmen der exemplarischen Vorgehensweise Exemplarische Vorgehensweise [: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)generiert wird:  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Customeditor-Kontextmenü\</ButtonText>  
  
 \<CommandName>Customeditor ContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Der obige Text fügt einen Kontextmenü Befehl mit dem **Kontextmenü des Texts customeditor**hinzu. Der Menü-GUID ist der Befehlssatz, der mit diesem Editor erstellt wird, und der Typ ist "Context".  
  
 Sie können auch vordefinierte Befehle verwenden, die nicht in der vsct-Datei definiert werden müssen. Wenn Sie z. b. die EditorPane.cs-Datei untersuchen, die von der Visual Studio-Paket Vorlage generiert wurde, stellen Sie fest, dass ein Satz vordefinierter Befehle, wie z. b. <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> von definiert, <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> in Befehls Handlern wie der onselectall-Methode behandelt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
