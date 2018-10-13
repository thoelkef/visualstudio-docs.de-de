---
title: Kontextmenüs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4b53174776b93d94c38982a430db3213ba184b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207726"
---
# <a name="context-menus"></a>Kontextmenüs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontextmenüs werden angezeigt, wenn ein Benutzer in ein aktiver Bereich des Clientbereichs mit der rechten Maustaste, und löschen, wenn die rechte Maustaste losgelassen wird.  
  
## <a name="editor-context-menus"></a>Editor-Kontextmenüs  
 Durch das Abfangen `ECMD_SHOWCONTEXTMENU`, der Sprachdienst kann steuern, die Kontextmenüs, die im Editor angezeigt werden. Um Ihr eigenes Kontextmenü anzuzeigen, behandeln Sie diesen Befehl beim übergeben in Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Wenn Sie diesen Befehl nicht behandeln, zeigt die IDE eine standard-Kontextmenü für den Editor bereitgestellt. Sie können auch den Inhalt der im Kontextmenü auf einer pro-Marker-Basis steuern. Weitere Informationen hierzu finden Sie unter [Textmarkierungen verwenden, mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md) und [Befehlen von Legacysprachdiensten abfangen](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)

