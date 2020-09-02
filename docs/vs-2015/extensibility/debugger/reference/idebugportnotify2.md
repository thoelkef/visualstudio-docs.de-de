---
title: IDebugPortNotify2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18edddd698953bf71febb8f9f2f1bac704205120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703924"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle registriert oder hebt die Registrierung eines Programms auf, das mit dem Port, auf dem er ausgeführt wird, deentschlbelt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen vom Port zu unterstützen. Sie wird in der Regel auf demselben Objekt implementiert, das die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) -Rückruf für die `IDebugPort2` Schnittstelle gibt diese Schnittstelle zurück. Außerdem gibt ein Aufrufen von [getportnotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) diese Schnittstelle zurück. Eine Debug-Engine kann diese Schnittstelle als Parameter für [watchforproviderevents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)sehen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortNotify2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das mit dem Port, auf dem er ausgeführt wird, dedeentschlbelt werden kann.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung eines Programms auf, das von dem Port, auf dem er ausgeführt wird, deentschlbelt werden kann.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Debugport nicht weiß, wann Programme geladen oder entladen werden, muss ein benutzerdefinierter Port Lieferant diese Schnittstelle implementieren. Alle Programme, die für das Debuggen über einen bestimmten Port geladen werden, werden über diese Schnittstelle nachverfolgt.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
