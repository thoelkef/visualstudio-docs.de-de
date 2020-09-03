---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722081"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Veraltet. Verwenden Sie nicht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parameter

`pbstrHostMachineName`\
vorgenommen Gibt den Namen des Computers zurück, auf dem das Programm ausgeführt wird.

## <a name="return-value"></a>Rückgabewert

Eine-Implementierung sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Ab Visual Studio 2005 wird diese Methode nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL` .

## <a name="see-also"></a>Weitere Informationen

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
