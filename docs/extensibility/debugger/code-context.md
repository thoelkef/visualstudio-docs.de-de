---
title: Codekontext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739149"
---
# <a name="code-context"></a>Codekontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein **Codekontext:**

- Stellt eine Abstraktion einer Position im Code bereit, wie sie dem Debugmodul (DE) bekannt ist. Für die meisten Laufzeitarchitekturen heute kann ein Codekontext als Adresse im Anweisungsstream eines Programms betrachtet werden. Bei nicht traditionellen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Codekontext auf andere Weise dargestellt werden.

- Beschreibt die aktuelle Position im Ausführungsstream des Programms, das Sie debuggen.

- Ist nur vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde.

- Verfügt über einen zugeordneten Dokumentkontext.

- Wird von einer [IDebugCodeContext2-Schnittstelle](../../extensibility/debugger/reference/idebugcodecontext2.md) implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Dokumentkontext](../../extensibility/debugger/document-context.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
