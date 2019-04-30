---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445287"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft die Hilfsprogramme für die Computer für einen Server an.  
  
> [!NOTE]
> Diese Methode ist veraltet: Verwenden Sie keine ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] gibt immer `E_NOTIMPL` , wenn diese Methode aufgerufen wird). Es wird aus historischen Gründen beibehalten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
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
