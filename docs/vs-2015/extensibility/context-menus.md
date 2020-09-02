---
title: Kontextmenüs | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184267"
---
# <a name="context-menus"></a>Kontextmenüs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontextmenüs werden angezeigt, wenn ein Benutzer mit der rechten Maustaste in einen aktiven Bereich des Client Bereichs klickt, und wenn die Rechte Maustaste losgelassen wird.  
  
## <a name="editor-context-menus"></a>Editor-Kontextmenüs  
 Durch das Abfangen `ECMD_SHOWCONTEXTMENU` kann der Sprachdienst die Kontextmenüs steuern, die im Editor angezeigt werden. Wenn Sie ein eigenes Kontextmenü anzeigen möchten, behandeln Sie diesen Befehl, wenn er an das-Steuerzeichen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von geleitet wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Wenn Sie diesen Befehl nicht ausführen, zeigt die IDE ein Standardkontext Menü an, das für den Editor bereitgestellt wird. Sie können den Inhalt des Kontextmenüs auch auf pro-Marker-Basis steuern. Weitere Informationen hierzu finden [Sie unter Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md) und [Abfangen von Legacy-Sprachdienst Befehlen](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines Legacy sprach Dienstanbieter](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
