---
title: IDebugProgramEx2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d3abc956d736f5c9273134b41c0fc9c2dc7db62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688944"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht es dem sitzungsdebug-Manager (SDM), an ein Programm anzufügen und den Programmknoten zu erhalten, der einem Programm zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle auf demselben Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle, damit die SDM an ein Programm angefügt werden kann, während gleichzeitig der Port Lieferant alle an das Programm angefügten Sitzungen verfolgen kann. Der benutzerdefinierte portlieferant kann diese Schnittstelle implementieren, wenn er Sie auswählt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Der SDM ruft [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine `IDebugProgram2` Schnittstelle auf, um diese Schnittstelle zu erhalten, um Sitzungen zu verfolgen, die an Programme angefügt sind.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramEx2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm an eine Sitzung an.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft den einem Programm zugeordneten Programmknoten ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle ist zwischen dem SDM und dem Programm privat.  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
