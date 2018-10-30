---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ef642e48ee4389e48c1141c18a70f9ad5d0b793
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949668"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Ruft die Anzahl der Zeichenfolgen, die für die angegebene Eigenschaft oder das Feld angezeigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `displayKind`  
 [in] Wert aus der [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) Enumeration.  
  
 `propertyOrField`  
 [in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die eine Eigenschaft oder ein Feld darstellt.  
  
 `pcelt`  
 [out] Gibt die Anzahl der anzuzeigenden Zeichenfolgen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)