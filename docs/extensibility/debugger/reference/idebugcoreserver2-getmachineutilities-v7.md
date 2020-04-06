---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733149"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Diese Methode ruft die Computerdienstprogramme für einen Server ab.

> [!NOTE]
> Diese Methode ist veraltet:[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] nicht `E_NOTIMPL` verwenden (wird immer zurückgegeben, wenn diese Methode aufgerufen wird). Es wird aus historischen Gründen beibehalten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parameter
`ppUtil`\
[out] Gibt `IDebugMDMUtil2_V7` eine Schnittstelle zurück, die die Informationen zu den Computerdienstprogrammen darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt `E_NOTIMPL`immer zurück, was darauf hinweist, dass die Methode nicht implementiert ist.

## <a name="remarks"></a>Bemerkungen
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]gibt `E_NOTIMPL` immer zurück, wenn diese Methode aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
