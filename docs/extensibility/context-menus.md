---
title: Kontextmenüs | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19838bbc1dfeeb0a0df9e1e1ce409557b6a28f1e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722365"
---
# <a name="context-menus"></a>Kontextmenüs
Kontextmenüs werden angezeigt, wenn ein Benutzer in ein aktiver Bereich des Clientbereichs mit der rechten Maustaste, und löschen, wenn die rechte Maustaste losgelassen wird.

## <a name="editor-context-menus"></a>Editor-Kontextmenüs
 Durch das Abfangen `ECMD_SHOWCONTEXTMENU`, der Sprachdienst kann steuern, die Kontextmenüs, die im Editor angezeigt werden. Um Ihr eigenes Kontextmenü anzuzeigen, behandeln Sie diesen Befehl beim übergeben in Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Wenn Sie diesen Befehl nicht behandeln, zeigt die IDE eine standard-Kontextmenü für den Editor bereitgestellt. Sie können auch den Inhalt der im Kontextmenü auf einer pro-Marker-Basis steuern. Weitere Informationen hierzu finden Sie unter [Textmarkierungen mit der legacy-API verwenden](../extensibility/using-text-markers-with-the-legacy-api.md) und [Abfangen von Befehlen von legacysprachdiensten ältere](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>Siehe auch
- [Entwickeln eines Datendiensts legacysprache](../extensibility/internals/developing-a-legacy-language-service.md)
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)