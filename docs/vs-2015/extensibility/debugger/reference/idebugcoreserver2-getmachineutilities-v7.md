---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft-Dokumentation
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
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecb460a070038d5a107f559e88be38381b11869c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822292"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft die Hilfsprogramme für die Computer für einen Server an.  
  
> [!NOTE]
>  Diese Methode ist veraltet: Verwenden Sie keine ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird). Es wird aus historischen Gründen beibehalten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUtil`  
 [out] Gibt eine `IDebugMDMUtil2_V7` -Schnittstelle, die Informationen für den Computer Dienstprogramme darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL`, gibt an, dass die Methode nicht implementiert wird.  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

