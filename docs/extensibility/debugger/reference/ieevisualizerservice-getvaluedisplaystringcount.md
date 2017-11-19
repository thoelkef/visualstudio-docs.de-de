---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fd3d05935c2edaeff723dc979764faf04d61c10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Ruft die Anzahl von Zeichenfolgen, die für die angegebene Eigenschaft oder das Feld angezeigt.  
  
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
 [in] Der Wert aus der [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) Enumeration.  
  
 `propertyOrField`  
 [in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle, eine Eigenschaft oder ein Feld darstellt.  
  
 `pcelt`  
 [out] Gibt die Anzahl der anzuzeigenden Zeichenfolgen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)