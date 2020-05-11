---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720706"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parameter
`riid`\
[in] GUID der zu erhaltenden Schnittstelle.

`ppvObject`\
[out] Gibt das Objekt zurück, das die gewünschte Schnittstelle implementiert. [C++] kann direkt in den gewünschten Schnittstellentyp gegossen werden. Verwenden Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um die gewünschte Schnittstelle abzubekommen.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugmodul im Prozessbereich ausgeführt wird und das zu debuggende Programm in einem eigenen Prozessbereich ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
