---
title: Code Kontext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97a4c8f8a9a710fab70760d9cb6eabb61de7a26f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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