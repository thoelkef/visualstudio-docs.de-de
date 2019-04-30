---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86c20e7c6828cfbf3ec31ba5dcbec9c7ee8478df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869359"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.

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

#### <a name="parameters"></a>Parameter
 `riid`

 [in] Die GUID der Schnittstelle abrufen.

 `ppvObject`

 [out] Gibt das Objekt, das die gewünschte Schnittstelle implementieren. [C++] dies direkt auf den Typ für die gewünschte Schnittstelle umgewandelt werden kann. [C#] verwenden Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um die gewünschte Schnittstelle abzurufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, wenn die Debug-Engine, in ausgeführt wird der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Prozessbereich und die zu debuggende Programm wird im eigenen Prozessbereich ausgeführt wird.

## <a name="see-also"></a>Siehe auch
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)