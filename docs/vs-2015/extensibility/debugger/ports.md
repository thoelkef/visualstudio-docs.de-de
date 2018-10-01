---
title: Ports | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbc8778af1cbc82b4f9e7f577a95123a1c1f5843
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512513"
---
# <a name="ports"></a>Ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Ports](https://docs.microsoft.com/visualstudio/extensibility/debugger/ports).  
  
Im Hinblick auf die Debugger-Architektur eine **Port**:  
  
-   Ist ein Container für eine Reihe von Prozessen auf einem Server ausgeführt werden. Beispielsweise kann ein Port eine Verbindung mit einem Windows CE-basierten Gerät durch ein serielles Kabel, oder auf einen Computer im Netzwerk nicht-DCOM darstellen. Ein spezieller Port wird aufgerufen, den lokalen Port, enthält alle auf dem lokalen Computer ausgeführten Prozesse.  
  
-   Kann sich selbst nach Name oder ID identifizieren.  
  
-   Können Auflisten aller Prozesse, die auf den Port ausgeführt wird, und starten und die folgenden Prozesse beendet.  
  
-   Wird durch dargestellt eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die übergeben wurde ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Argument [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Stellt einen Standardport, der alle Windows-basierten Prozesse systemeigenen und verwalteten behandelt. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten implementiert werden, die nicht Windows-basiert sind. Um diese benutzerdefinierte Ports angeben, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

