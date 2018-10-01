---
title: IEnumDebugPorts2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ff7eac1da5cba43bf93a352e571c7a1f912932b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522530"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IEnumDebugPorts2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugports2).  
  
Diese Schnittstelle Listet die Ports von einem Computer oder Port-Lieferanten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um eine Liste der Ports, die von den Lieferanten erstellten darstellen. Visual Studio implementiert diese Schnittstelle zur Unterstützung von eigenen portbereitstellers.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) beim Abrufen der diese Schnittstelle, die eine Liste der Ports, die von den Anschlusslieferanten erstellt darstellt. Rufen Sie [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) , rufen Sie diese Schnittstelle stellt eine Liste von Ports, die gespeichert wurden auf dem Datenträger.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugPorts2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Ruft eine angegebene Anzahl von Ports in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Überspringt eine angegebene Anzahl von Ports in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ruft die Anzahl der Ports in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio verwendet diese Schnittstelle können Sie eine Liste der Ports, die zum Anhängen an Prozesse aufzufüllen.  
  
 Eine Debug-Engine verwendet diese Schnittstelle in der Regel nicht.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

