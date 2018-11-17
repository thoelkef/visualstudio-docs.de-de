---
title: Dokumentieren Sie Kontext | Microsoft-Dokumentation
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
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5753e2353b351f6aa4bd73c5aced3d4959b3cde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741189"
---
# <a name="document-context"></a>Dokumentkontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen, eine **Dokumentkontext**:  
  
-   Stellt eine Position in einer Quelldatei dar. Für Sprachen, in dem die Quelldatei nicht vorhanden sein kann, gibt ein Dokumentenkontext eine Position in einem Dokument, das von der Runtime-Umgebung in der Regel generiert. Beispielsweise kann eine Skript-Engine ein Dokument vom Skript generieren. Weitere Informationen finden Sie unter [Dokumentposition](../../extensibility/debugger/document-position.md).  
  
-   Beschreibt eine Position in einem Quelldokument, das einen Codekontext entspricht. Der Symbol-Handler einen Codekontext Dokumentation Kontext mithilfe der Informationen, die vom eines Compilers oder Interpreters zugeordnet.  
  
-   Wird implementiert, indem ein [idebugdocumentcontext2 angegeben](../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)   
 [Symbolanbieterschnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)

