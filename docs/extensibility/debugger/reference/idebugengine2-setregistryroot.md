---
title: IDebugEngine2::SetRegistryRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beba304e846126b262c23c0fc8232f79de5fd794
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730872"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Legt den Registrierungsstamm für das Debugmodul (DE) fest.

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

## <a name="parameters"></a>Parameter
`pszRegistryRoot`\
[in] Der zu verwendende Registrierungsstamm.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ermöglicht es, einen alternativen Registrierungsstamm anzugeben, den die DE zum Abrufen von Registrierungseinstellungen verwenden soll. z. B. "HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp".

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
