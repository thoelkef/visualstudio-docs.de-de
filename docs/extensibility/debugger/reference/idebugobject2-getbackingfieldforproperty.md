---
title: 'IDebugObject2:: getbackingfieldforproperty | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726244"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ruft das Feld oder die Variable (sofern vorhanden) ab, die möglicherweise die von diesem-Objekt dargestellte Eigenschaft unterstützt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parameter
`ppObject`\
vorgenommen Ein [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) -Objekt, das das Unterstützungs Feld beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) -Objekt stellt eine Eigenschaft der verwalteten Code Klasse dar, d. h. eine Methode mit einem Get-und/oder Set-Accessor. Diese Eigenschaften erfordern im Allgemeinen, dass eine Variable den von der-Eigenschaft bearbeiteten Wert enthält. Diese Variable wird als dahinter liegendes Feld bezeichnet. Wenn kein dahinter liegendes Feld für das Objekt vorhanden ist, stellen Sie sicher, dass Sie einen NULL-Wert zurückgeben: einige Aufrufer achten möglicherweise nicht auf den Rückgabewert, sondern sehen stattdessen, ob ein NULL-Wert in zurückgegeben wurde `ppObject` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
