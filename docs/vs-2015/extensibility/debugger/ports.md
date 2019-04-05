---
title: Ports | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955602"
---
# <a name="ports"></a>Ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur eine **Port**:  
  
- Ist ein Container für eine Reihe von Prozessen auf einem Server ausgeführt werden. Beispielsweise kann ein Port eine Verbindung mit einem Windows CE-basierten Gerät durch ein serielles Kabel, oder auf einen Computer im Netzwerk nicht-DCOM darstellen. Ein spezieller Port wird aufgerufen, den lokalen Port, enthält alle auf dem lokalen Computer ausgeführten Prozesse.  
  
- Kann sich selbst nach Name oder ID identifizieren.  
  
- Können Auflisten aller Prozesse, die auf den Port ausgeführt wird, und starten und die folgenden Prozesse beendet.  
  
- Wird durch dargestellt eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die übergeben wurde ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Argument [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Stellt einen Standardport, der alle Windows-basierten Prozesse systemeigenen und verwalteten behandelt. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten implementiert werden, die nicht Windows-basiert sind. Um diese benutzerdefinierte Ports angeben, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
