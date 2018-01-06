---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords: IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bf5881dabea216d7226e731c169dd97d1460c7fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Diese Methode ruft die Hilfsprogramme für die Computer für einen Server an.  
  
> [!NOTE]
>  Diese Methode ist veraltet: Verwenden Sie keine ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird). Es wird aus Verlaufsgründen beibehalten.  
  
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
 [out] Gibt eine `IDebugMDMUtil2_V7` -Schnittstelle, die Informationen für den Computer Hilfsprogramme darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL`, gibt an, dass die Methode nicht implementiert ist.  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)