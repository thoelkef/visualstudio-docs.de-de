---
title: IDebugProgramNode2::GetProgramName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9af930716725a62fff5ea3d1635b506b06b26086
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721995"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Ruft den Namen des Programms ab.

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

## <a name="parameters"></a>Parameter
`pbstrProgramName`\
[out] Gibt den Namen des Programms zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Der Name eines Programms ist nicht derselbe wie der Pfad zum Programm, obwohl der Name des Programms Teil eines solchen Pfads sein kann.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CProgram` Methode für ein einfaches Objekt implementiert wird, das die [IDebugProgramNode2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert. Die `MakeBstr` Funktion ordnet eine Kopie der angegebenen Zeichenfolge als BSTR zu.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
