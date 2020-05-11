---
title: Hafenlieferanten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738293"
---
# <a name="port-suppliers"></a>Hafenlieferanten
In der Debuggerarchitektur wird ein *Portlieferant:*

- Wird von einem Server enthalten und stellt ports auf Anfrage an diesen Server bereit.

- Kann Ports hinzufügen und vom enthaltenden Server entfernen.

- Kann alle Ports aufzählen, die er dem Server zur Verfügung gestellt hat.

- Wird durch eine [IDebugPortSupplier2-Schnittstelle](../../extensibility/debugger/reference/idebugportsupplier2.md) dargestellt, die über die Registrierung bei Visual Studio registriert ist. Diese Schnittstelle kann durch Aufrufen von [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)abgerufen werden.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]stellt einen Standardportlieferanten und einen Standardport bereit. Wenn ein benutzerdefinierter Port implementiert werden muss, muss auch ein benutzerdefinierter Portlieferant implementiert werden, um diese benutzerdefinierten Ports zu versorgen.

## <a name="see-also"></a>Weitere Informationen
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
