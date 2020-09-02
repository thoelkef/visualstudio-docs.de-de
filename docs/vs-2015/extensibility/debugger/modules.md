---
title: Module | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153747"
---
# <a name="modules"></a>Module
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Modul**:  
  
- Ist ein physischer Container von Code, z. b. eine ausführbare Datei oder eine DLL.  
  
- Kann seine Symbole erneut laden und sich selbst beschreiben. Modulbeschreibungen werden im Fenster "Module" der IDE angezeigt.  
  
- Wird durch eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) -Schnittstelle dargestellt, die von einem Debug-Modul erstellt wurde, um das Modul zu beschreiben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
