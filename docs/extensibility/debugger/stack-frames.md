---
title: Stapel Rahmen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712842"
---
# <a name="stack-frames"></a>Stapelrahmen
In der Debuggerarchitektur wird ein *Stackframe*:

- Eine Abstraktion eines Stapels, die den Ausführungskontext eines Threads bereitstellt. Ein Thread wird immer innerhalb einer Funktion ausgeführt. Ein Stapelrahmen enthält die lokalen Variablen der Funktion und die Argumente dazu. Zum Debuggen mit Visual Studio muss die zu debuggende Sprache oder Umgebung Stackframes unterstützen.

- Kann sich selbst identifizieren und beschreiben und den zugeordneten Thread zurückgeben. Ein Stapelrahmen kann auch den Codekontext zurückgeben, der den aktuellen Anweisungszeiger und die zugehörigen Dokumentations- und Ausdrucksauswertungskontexte darstellt.

- Verfügt über Eigenschaften, die den Namen, typ und den Wert lokaler Variablen und Argumente beschreiben und in verschiedenen IDE-Debugfenstern angezeigt werden.

- Wird durch eine [IDebugStackFrame2-Schnittstelle](../../extensibility/debugger/reference/idebugstackframe2.md) dargestellt, die in der Regel von einem Debugmodul (DE) oder einer virtuellen Maschine als Folge der Ausführung eines Threads erstellt wird.

## <a name="see-also"></a>Weitere Informationen
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
