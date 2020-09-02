---
title: Idebugprocessqueryproperties | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad6e7d10b2a6a83aa11a0296f4804704cd12c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537250"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle ist eine von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Implementierern implementierte Erweiterungsschnittstelle. Sie ermöglicht es dem Implementierer, Informationen zur debugprozessumgebung zu erhalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Implementieren Sie diese Schnittstelle, um Informationen zur Ausführungsumgebung eines Debugprozesses zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcessQueryProperties` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Fragt nach einem Eigenschafts Wert ab.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Fragt nach Eigenschafts Werten ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle ist selten implementiert.  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
