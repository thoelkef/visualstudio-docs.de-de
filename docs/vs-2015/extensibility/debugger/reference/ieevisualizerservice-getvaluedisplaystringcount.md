---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 412a2585a35c7503f99207050d07d3b27d434e99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764056"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl der Zeichenfolgen, die für die angegebene Eigenschaft oder das Feld angezeigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

