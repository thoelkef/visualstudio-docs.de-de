---
title: IDebugEngine2::SetRegistryRoot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761a8509958c60746f7e5312fa5f5e13631acc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698806"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Legt den Registrierungsstamm für die Debug-Engine (DE) fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

#### <a name="parameters"></a>Parameter
 `pszRegistryRoot`

 [in] Der Registrierungsstamm verwenden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Mit dieser Methode können [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] an einen alternativen Registrierungsstamm, die die DE, zum Abrufen von registrierungseinstellungen verwenden soll; z. B. "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)