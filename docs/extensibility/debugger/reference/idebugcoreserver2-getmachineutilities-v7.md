---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 265c5b414c53fb6dfe43f63c1016204b8ff02c81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908664"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Diese Methode ruft die Hilfsprogramme für die Computer für einen Server an.  
  
> [!NOTE]
>  Diese Methode ist veraltet: Verwenden Sie keine ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird). Es wird aus historischen Gründen beibehalten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)