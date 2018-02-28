---
title: "Kontextmenüs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 69048a35514ac35556e04ed5266ff58b21b31e0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="context-menus"></a>Kontextmenüs
Kontextmenüs werden angezeigt, wenn ein Benutzer in einem aktiven Bereich des Clientbereichs klickt und zu löschen, wenn die rechte Maustaste losgelassen wird.  
  
## <a name="editor-context-menus"></a>Editor-Kontextmenüs  
 Durch Abfangen `ECMD_SHOWCONTEXTMENU`, Ihre Sprachdienst kann steuern, die Kontextmenüs, die im Editor angezeigt werden. Um eine eigene Kontextmenü anzuzeigen, diesen Befehl beim Behandeln übergeben wird Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Wenn Sie diesen Befehl nicht behandelt, zeigt die IDE eine standard-Kontextmenü für den Editor bereitgestellt. Sie können auch den Inhalt des Kontextmenüs auf Basis eines pro-Marker steuern. Weitere Informationen hierzu finden Sie unter [mithilfe von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md) und [abfangen Legacy-Dienst Sprachbefehle](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von einem Legacy-Sprachdienst](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)