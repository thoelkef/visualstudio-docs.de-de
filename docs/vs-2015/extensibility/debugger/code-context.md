---
title: Code Kontext | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197378"
---
# <a name="code-context"></a>Codekontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen ein **Code Kontext**:  
  
- Stellt eine Abstraktion einer Position im Code bereit, wie Sie der Debug-Engine (de) bekannt ist. Für die meisten Lauf Zeit Architekturen kann ein Code Kontext als Adresse im Anweisungs Datenstrom eines Programms betrachtet werden. Bei nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, kann ein Code Kontext auf andere Weise dargestellt werden.  
  
- Beschreibt die aktuelle Position im Ausführungsdaten Strom des Programms, das gedebuggt wird.  
  
- Ist nur vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde.  
  
- Verfügt über einen zugeordneten Dokument Kontext.  
  
- Wird von einer [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) -Schnittstelle implementiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dokument Kontext](../../extensibility/debugger/document-context.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
