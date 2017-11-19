---
title: Ports | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 926f5e9a80a91da57d843c11175865f78775e38c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ports"></a>Ports
Im Hinblick auf die Architektur des Debuggers einen **Port**:  
  
-   Ist ein Container für eine Gruppe von Prozessen auf einem Server ausgeführt werden. Beispielsweise kann ein Port eine Verbindung mit einem Windows CE-basierten Gerät durch eine serielle Kabel oder an einen Computer im Netzwerk nicht von DCOM darstellen. Eine spezielle Port, den lokalen Port aufgerufen enthält alle auf dem lokalen Computer ausgeführten Prozesse an.  
  
-   Können sich nach Name oder Bezeichner identifizieren.  
  
-   Können alle auf den Port ausgeführten Prozesse auflisten und starten diese Prozesse zu beenden.  
  
-   Wird durch dargestellt ein [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die durch Übergabe erstellt wird ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Argument [hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Stellt einen Standardport, der alle Windows-basierten Prozessen, systemeigenen und verwalteten behandelt. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten implementiert werden, die nicht Windows-basiert sind. Um eine solche benutzerdefinierte Ports angeben, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)