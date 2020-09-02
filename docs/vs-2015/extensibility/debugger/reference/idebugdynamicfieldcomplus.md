---
title: Idebugdynamicfieldcomplus | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 71756b4c4df0768520f72219cf50e5407604635d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198500"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt ein dynamisches Feld für ein [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [idebugdynamicfield](../../../extensibility/debugger/reference/idebugdynamicfield.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Ruft einen Typ ab, der den primitiven Typ erhält.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Ruft einen Typ ab, der sein Token erhält.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
