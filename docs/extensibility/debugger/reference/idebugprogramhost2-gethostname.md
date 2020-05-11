---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722234"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ruft den Titel, den Anzeigenamen oder den Dateinamen des Hostingprozesses dieses Programms ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parameter
`dwType`\
[in] Ein Wert [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) aus der GETHOSTNAME_TYPE-Enumeration.

`pbstrHostName`\
[out] Gibt den angeforderten Namen des Hostingprozesses zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In einer typischen Implementierung `dwType` dieser Methode wird der Parameter ignoriert, und ein Anzeigename des Hostcomputers wird zurückgegeben. Eine weitere mögliche Implementierung `dwType` besteht darin, den Parameter an einen Aufruf der [GetHostName-Methode](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) zu übergeben, um den Namen abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
