---
title: Code-Kontext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88bdd673de5ef8d8339dabf1c19618ea8e3faa44
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215578"
---
# <a name="code-context"></a>Codekontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen, eine **Codekontext**:  
  
-   Stellt eine Abstraktion einer Position im Code bereit, wie die Debug-Engine (DE) bekannt. Für die meisten Laufzeit-Architekturen kann heute ein Codekontext als eine Adresse im Anweisungsstream eines Programms betrachtet werden. Für nicht traditionelle Sprachen, in dem Code nicht von Anweisungen dargestellt werden kann, kann ein Codekontext andere Weise dargestellt werden.  
  
-   Beschreibt die aktuelle Position im Stream Ausführung des gedebuggten Programms.  
  
-   Ist vorhanden, nur, wenn ein Programm an einem Haltepunkt beendet wurde.  
  
-   Verfügt über einen zugehörigen Dokumentkontext.  
  
-   Wird implementiert, indem ein [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)

