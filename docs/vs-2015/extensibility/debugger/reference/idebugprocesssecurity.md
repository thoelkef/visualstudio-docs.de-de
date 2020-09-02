---
title: Idebugprocesssecurity | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 836b971963587aa89440c6e023ee255612d2a087
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187945"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` wird von einem Port Lieferanten implementiert, um den Benutzer zu warnen, dass das Anfügen an den Prozess unsicher ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcessSecurity` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ruft den Benutzernamen vom Port Lieferanten ab.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Warnt einen Benutzer, dass das Anhängen an den Debugprozess unsicher ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Implementieren Sie diese Schnittstelle, um eine Warnung anzuzeigen und dem Benutzer zu gestatten, abzubrechen, wenn der Prozess, an den Sie anhängen, als unsicher eingestuft werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Landungen](../../../extensibility/debugger/ports.md)   
 [Port Lieferanten](../../../extensibility/debugger/port-suppliers.md)   
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
