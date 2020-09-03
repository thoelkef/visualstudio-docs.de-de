---
title: Threads | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712478"
---
# <a name="threads"></a>Threads
In der Debugger-Architektur ein *Thread*:

- Ist die grundlegende Einheit der Berechnung. Ein Thread führt seine Anweisungen sequenziell innerhalb des Kontexts einer einzelnen Rückruf Stapel aus und wechselt von einem Code Kontext zum nächsten.

- Kann sich selbst und das Programm identifizieren, in dem es ausgeführt wird. Threads können benannt, angehalten und fortgesetzt werden. Ein Thread kann auch seine zugeordneten Stapel Rahmen auflisten und unter bestimmten Bedingungen in einen anderen Stapel Rahmen verschieben. Bei einem Kontext eines Stapel Rahmens kann ein Thread ggf. den zugeordneten logischen Thread zurückgeben. Ein Thread verfügt über Eigenschaften, z. b. eine Unterbrechungs Anzahl **, die im Thread Fenster der** IDE angezeigt werden kann.

- Wird durch eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Schnittstelle dargestellt, die in der Regel durch eine Debug-Engine (de) oder eine virtuelle Maschine erstellt wird, wenn ein Programm ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md)
