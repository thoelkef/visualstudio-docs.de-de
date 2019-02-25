---
title: IDebugDocument2::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f1ef243afd607a565e2c7a8e6f557f0b9906c86
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701016"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ruft den Namen des Dokuments in einem von mehreren Formaten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

#### <a name="parameters"></a>Parameter
 `gnType`

 [in] Ein Wert aus der [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) -Enumeration, den Typ des Namens zurückzugebenden bestimmt.

 `pbstrFileName`

 [out] Gibt eine Zeichenfolge, die den Namen des Dokuments enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode kann z. B. den Namen des Dokuments als einen Titel oder als ein Dateiname oder sogar einen Dateinamen zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)