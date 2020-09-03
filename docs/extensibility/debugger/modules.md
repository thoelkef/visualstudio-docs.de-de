---
title: Module | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738345"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur ist ein *Modul*:

- Ist ein physischer Container von Code, z. b. eine ausführbare Datei oder eine DLL.

- Kann seine Symbole erneut laden und sich selbst beschreiben. Modulbeschreibungen werden im Fenster "Module" der IDE angezeigt.

- Wird durch eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle dargestellt, die von einem Debug-Modul erstellt wurde, um das Modul zu beschreiben.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
