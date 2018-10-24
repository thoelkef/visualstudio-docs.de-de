---
title: IEnumDebugAddresses::Clone | Microsoft-Dokumentation
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
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38f181d6a9da3919753ea13361d16ff60efba107
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827517"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt eine Kopie der aktuellen Enumeration als separates Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Kopie der Enumeration hat den gleichen Zustand wie die ursprüngliche, zu dem Zeitpunkt, die diese Methode aufgerufen wird. Allerdings wird der Kopiervorgangs des und den ursprünglichen Zustand sind getrennt und einzeln geändert werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

