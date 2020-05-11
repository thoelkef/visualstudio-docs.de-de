---
title: Häfen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738306"
---
# <a name="ports"></a>Ports
In der Debuggerarchitektur wird ein *Port*:

- Ein Container für eine Reihe von Prozessen, die auf einem Server ausgeführt werden. Ein Port kann z. B. eine Verbindung zu einem Windows CE-basierten Gerät über ein serielles Kabel oder zu einem vernetzten Nicht-DCOM-Computer darstellen. Ein spezieller Port, der als lokaler Port bezeichnet wird, enthält alle Prozesse, die auf dem lokalen Computer ausgeführt werden.

- Kann sich durch Namen oder Bezeichner identifizieren.

- Kann alle Prozesse aufzählen, die auf dem Port ausgeführt werden, und diese Prozesse starten und beenden.

- Wird durch eine [IDebugPort2-Schnittstelle](../../extensibility/debugger/reference/idebugport2.md) dargestellt, die durch Übergeben eines [IDebugPortRequest2-Arguments](../../extensibility/debugger/reference/idebugportrequest2.md) an [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)erstellt wird.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]stellt einen Standardport ein, der alle windows-basierten Prozesse verarbeitet, sowohl systemeigene als auch verwaltete. Für Verbindungen mit externen Geräten, die nicht Windows-basiert sind, muss ein benutzerdefinierter Port eingerichtet werden. Um solche benutzerdefinierten Ports zu liefern, müssen Sie auch einen benutzerdefinierten Portlieferanten einrichten.

## <a name="see-also"></a>Weitere Informationen
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
