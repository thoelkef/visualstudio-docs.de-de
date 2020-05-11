---
title: Haltepunkte (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739193"
---
# <a name="breakpoints-visual-studio-sdk"></a>Haltepunkte (Visual Studio SDK)
Es gibt drei Arten von Haltepunkten: ausstehend, gebunden und Fehler.

 **Ein ausstehender Haltepunkt:**

- Eine Abstraktion, die alle Informationen enthält, die zum Binden eines Haltepunkts an einen oder mehrere Codekontexte in einem oder mehreren Programmen erforderlich sind. Jedes Mal, wenn ein zu debuggden Programm code lädt, überprüft das Debugmodul alle ausstehenden Haltepunkte, um festzustellen, ob sie gebunden werden können.

   Ein ausstehender Haltepunkt selbst bindet nie an Code, sondern sammelt und soll alle gebundenen Haltepunkte enthalten, die er generiert.

- Wird durch eine [IDebugPendingBreakpoint2-Schnittstelle](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) dargestellt.

  **Ein gebundener Haltepunkt:**

- Eine Abstraktion für einen Haltepunkt, der einem einzelnen Codekontext zugeordnet oder an einen einzelnen Codekontext gebunden ist. Jeder gebundene Haltepunkt wird als Reaktion auf einen ausstehenden Haltepunkt generiert. Ein ausstehender Haltepunkt kann jedoch mehr als einen gebundenen Haltepunkt generieren.

   Wenn Code entladen wird, kann ein gebundener Haltepunkt ungebunden und verworfen werden.

- Wird durch eine [IDebugBoundBreakpoint2-Schnittstelle](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) dargestellt.

  **Ein Fehlerhaltepunkt:**

- Eine Abstraktion zum Beschreiben eines Fehlers beim Versuch, einen ausstehenden Haltepunkt an einen Codekontext zu binden. Ein Fehlerhaltepunkt beschreibt entweder einen Fehler an der Position oder im Haltepunktausdruck selbst. Weitere Informationen finden Sie unter Binden von [Haltepunkten](../../extensibility/debugger/binding-breakpoints.md).

   Der Haltepunktfehler kann entweder ein Fehler oder eine Warnung sein.

- Wird durch eine [IDebugErrorBreakpoint2-Schnittstelle](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) dargestellt.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Codekontext](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
