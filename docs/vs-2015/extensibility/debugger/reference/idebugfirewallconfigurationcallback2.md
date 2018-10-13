---
title: IDebugFirewallConfigurationCallback2 | Microsoft-Dokumentation
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
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eadd21622c7db2415d0170d252b3641e8bde927b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206208"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ermöglicht es eine Debug-Engine, die DCOM verwendet wird, stellen die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche, um sicherzustellen, dass die Firewall das Remotedebugging nicht blockiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Durch die Port-Objekt, von der Sitzungs-Manager implementiert.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugFirewallConfigurationCallback2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Fordert an, dass der Firewall kein Remotedebugging blockiert.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

