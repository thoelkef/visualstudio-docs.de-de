---
title: Code-Kontext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31b1f3d91fd44308c1737f8066c13af730454abe
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203344"
---
# <a name="code-context"></a>Codekontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine **Codekontext**:  
  
-   Stellt eine Abstraktion einer Position im Code bereit, wie die Debug-Engine (DE) bekannt. Für die meisten Laufzeit-Architekturen kann heute ein Codekontext als eine Adresse im Anweisungsstream eines Programms betrachtet werden. Für nicht traditionelle Sprachen, in dem Code nicht von Anweisungen dargestellt werden kann, kann ein Codekontext andere Weise dargestellt werden.  
  
-   Beschreibt die aktuelle Position im Stream Ausführung des Programms, die Sie debuggen.  
  
-   Ist vorhanden, nur, wenn ein Programm an einem Haltepunkt beendet wurde.  
  
-   Verfügt über einen zugehörigen Dokumentkontext.  
  
-   Wird implementiert, indem ein [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)