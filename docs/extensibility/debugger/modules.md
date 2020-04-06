---
title: Module | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738345"
---
# <a name="modules"></a>Module
In Bezug auf die Debugger-Architektur, ein *Modul*:

- Ein physischer Codecontainer, z. B. eine ausführbare Datei oder eine DLL.

- Kann seine Symbole neu laden und sich selbst beschreiben. Modulbeschreibungen werden im Modulfenster der IDE angezeigt.

- Wird durch eine [IDebugModule2-Schnittstelle](../../extensibility/debugger/reference/idebugmodule2.md) dargestellt, die von einem Debugmodul erstellt wird, um das Modul zu beschreiben.

## <a name="see-also"></a>Weitere Informationen
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
