---
title: Kontextmenüs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa957e949127663eca7d4e619919edcc07c7a29b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="context-menus"></a>Kontextmenüs
Kontextmenüs werden angezeigt, wenn ein Benutzer in einem aktiven Bereich des Clientbereichs klickt und zu löschen, wenn die rechte Maustaste losgelassen wird.  
  
## <a name="editor-context-menus"></a>Editor-Kontextmenüs  
 Durch Abfangen `ECMD_SHOWCONTEXTMENU`, Ihre Sprachdienst kann steuern, die Kontextmenüs, die im Editor angezeigt werden. Um eine eigene Kontextmenü anzuzeigen, diesen Befehl beim Behandeln übergeben wird Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Wenn Sie diesen Befehl nicht behandelt, zeigt die IDE eine standard-Kontextmenü für den Editor bereitgestellt. Sie können auch den Inhalt des Kontextmenüs auf Basis eines pro-Marker steuern. Weitere Informationen hierzu finden Sie unter [mithilfe von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md) und [abfangen Legacy-Dienst Sprachbefehle](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von einem Legacy-Sprachdienst](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)