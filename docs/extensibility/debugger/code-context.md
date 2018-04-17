---
title: Code Kontext | Microsoft Docs
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
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>Codekontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine **Codekontext**:  
  
-   Stellt eine Abstraktion einer Position im Code bereit, da die Debugging-Modul (DE) bekannt. Für die meisten-Laufzeit-Architekturen kann heute ein Codekontext als eine Adresse in den Anweisungsstream ein Programm betrachtet werden. Für die traditionelle Sprachen, in dem Code nicht durch Anweisungen dargestellt werden kann, kann ein Codekontext anderweitig dargestellt werden.  
  
-   Beschreibt die aktuelle Position im Stream Ausführung des Programms, der debuggt wird.  
  
-   Existiert nur, wenn ein Programm an einem Haltepunkt angehalten wurde.  
  
-   Verfügt über einen Kontext zugeordnete Dokument.  
  
-   Wird implementiert, indem ein [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentenkontext](../../extensibility/debugger/document-context.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)