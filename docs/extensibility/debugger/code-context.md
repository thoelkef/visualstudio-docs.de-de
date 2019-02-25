---
title: Code-Kontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 114537976561e72a9b1922c41d94ffa5e7ce613b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714543"
---
# <a name="code-context"></a>Codekontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine **Codekontext**:

-   Stellt eine Abstraktion einer Position im Code bereit, wie die Debug-Engine (DE) bekannt. Für die meisten Laufzeit-Architekturen kann heute ein Codekontext als eine Adresse im Anweisungsstream eines Programms betrachtet werden. Für nicht traditionelle Sprachen, in dem Code nicht von Anweisungen dargestellt werden kann, kann ein Codekontext andere Weise dargestellt werden.

-   Beschreibt die aktuelle Position im Stream Ausführung des Programms, die Sie debuggen.

-   Ist vorhanden, nur, wenn ein Programm an einem Haltepunkt beendet wurde.

-   Verfügt über einen zugehörigen Dokumentkontext.

-   Wird implementiert, indem ein [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Dokumentkontext](../../extensibility/debugger/document-context.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)