---
title: IDebugQueryEngine2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7274d621e47c9c705cc0ce6bc4ad49f24e144f59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683278"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht es dem sitzungsdebug-Manager (SDM), eine Schnittstelle abzurufen, die die Debug-Engine (de) darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die de implementiert diese Schnittstelle für die Objekte, die die gängigsten de-Schnittstellen implementieren (z. b. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)und [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)), um den Zugriff auf die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle der de selbst zuzulassen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine typische de-Schnittstelle auf, um diese Schnittstelle abzurufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugQueryEngine2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft eine benutzerdefinierte Debug-Engine-Schnittstelle (de) ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird in der Regel in dem Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle implementiert, um Kausalität geordnete schrittweise durchlaufen von Funktionen zu unterstützen. Das heißt, wenn der Debugger eine Funktion ausführt, ist die nächste auszuführende Funktion möglicherweise nicht die vorherige Funktion auf dem Stapel, sondern eine Funktion in einem anderen Thread. Eine Definition der "Kausalität" finden Sie im [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
