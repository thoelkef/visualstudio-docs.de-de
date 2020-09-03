---
title: IDebugProgramDestroyEventFlags2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182215"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ermöglicht es einer Debug-Engine, das Standardverhalten der Benutzeroberfläche zu überschreiben, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Wenn Sie eine Debugsitzung beenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Debug-engines implementiert. Dies ist nützlich für Hosts, die möglicherweise mehrere Programme während der Lebensdauer eines Prozesses erstellen und zerstören.  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramDestroyEventFlags2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft die Flags für die Programm Zerstörung ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Standardverhalten der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche besteht darin, zurück in den Entwurfs Modus zu wechseln, nachdem alle Programme ein Programm zerstörungsereignis gesendet haben. Diese Schnittstelle ermöglicht es einer Debug-Engine, dieses Verhalten zu ändern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
