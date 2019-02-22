---
title: IDebugProgramNode2::GetProgramName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6f678adc135e85f8808cef36d819733033447e4
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450372"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Ruft den Namen des Programms.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

#### <a name="parameters"></a>Parameter
`pbstrProgramName`  
[out] Gibt den Namen des Programms.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Der Name eines Programms ist nicht dasselbe wie der Pfad für das Programm, obwohl der Name des Programms Teil von einem derartigen Pfad sein kann.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CProgram` Objekt, das implementiert die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle. Die `MakeBstr` Funktion weist eine Kopie der angegebenen Zeichenfolge als BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
