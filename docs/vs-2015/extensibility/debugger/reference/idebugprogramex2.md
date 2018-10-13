---
title: IDebugProgramEx2 | Microsoft-Dokumentation
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
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb8009203a4d97ef5ecce37751495300b3b9248c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241519"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle kann die Sitzung, die Debug-Manager (SDM) Anfügen an ein Programm und den Programm Knoten mit einem Programm verknüpft.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle auf dasselbe Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um das SDM an ein Programm angefügt werden soll, während gleichzeitig an ermöglicht Anschlusslieferanten zum Nachverfolgen von allen Sitzungen angefügt ermöglichen die das Programm. Benutzerdefinierte Anschlusslieferanten kann diese Schnittstelle implementieren, wenn er entscheidet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die SDM-Aufrufe [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine `IDebugProgram2` Schnittstelle zum Abrufen diese Schnittstelle, um Sitzungen zu verfolgen, die Programme angefügt haben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramEx2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm mit einer Sitzung.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft ab, der Programm-Knoten, die mit einem Programm verknüpft.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist privat zwischen den SDM und dem Programm.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

