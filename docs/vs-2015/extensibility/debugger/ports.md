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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153688"
---
# <a name="ports"></a>Ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ein **Port**:  
  
- Ist ein Container für eine Gruppe von Prozessen, die auf einem Server ausgeführt werden. Ein Port kann z. b. eine Verbindung mit einem Windows CE basierten Gerät durch ein serielles Kabel oder einen vernetzten nicht-DCOM-Computer darstellen. Ein spezieller Port, der als lokaler Port bezeichnet wird, enthält alle Prozesse, die auf dem lokalen Computer ausgeführt werden.  
  
- Kann sich selbst anhand des Namens oder Bezeichners identifizieren.  
  
- Kann alle Prozesse auflisten, die auf dem Port ausgeführt werden, und diese Prozesse starten und beenden.  
  
- Wird durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle dargestellt, die durch Übergeben eines [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) -Arguments an [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)erstellt wird.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stellt einen Standardport bereit, der alle Windows-basierten Prozesse, System eigen und verwaltet, verarbeitet. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten implementiert werden, die nicht auf Windows basieren. Zum Bereitstellen dieser benutzerdefinierten Ports muss auch ein benutzerdefinierter Port Lieferant implementiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Webserver](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
