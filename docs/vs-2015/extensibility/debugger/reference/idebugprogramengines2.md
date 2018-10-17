---
title: IDebugProgramEngines2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee89f8ba02ac3aac0f61dabbaacb1be6742067bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235065"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird von programmknoten verwendet, die alle möglichen Debug-Engines (DE) an, die dieses Programm debuggen können.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein DE oder einen benutzerdefinierten Port Lieferanten für das gleiche Objekt, das implementiert diese Schnittstelle implementiert [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) zur Unterstützung einer bestimmten DE Verwendung für ein bestimmtes Programm herstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine `IDebugProgramNode2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramEngines2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Gibt an, die mögliche DEs, den das Programm debuggen können.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wählt die DE für das Debuggen dieses Programms verwendet.|  
  
## <a name="remarks"></a>Hinweise  
 Nach eine bereitgestellten Kompatibilitätsrichtlinie, die vom Benutzer ausgewählt wird, wird diese Entscheidung mit dem Programm Knoten durch den Aufruf registriert [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Die ausgewählten-Engine wird die Engine zurückgegebenes [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)

