---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732560"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ruft die benutzerdefinierten Attributbytes ab, die den Namen des benutzerdefinierten Attributs erhalten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parameter
`pszCustomAttributeName`\
[in] Eine Zeichenfolge, die den Namen des benutzerdefinierten Attributs enthält, nach dem gesucht werden soll.

`ppBlob`\
[in, out] Ein Array, das mit den benutzerdefinierten Attributbytes ausgefüllt wird.

`pdwLen`\
[in, out] Gibt die maximale Anzahl von Bytes `ppBlob` an, die im Array zurückgegeben werden sollen, und gibt die Anzahl der Bytes zurück, die tatsächlich in das Array geschrieben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn das benutzerdefinierte Attribut nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Legen `ppBlob` Sie den Parameter auf einen Nullwert fest, um die Anzahl der verfügbaren Attribute bytes zurückzugeben. Weisen Sie dann ein Array zu, und übergeben Sie dieses Array für den `ppBlob` Parameter.

 Die Attributbytes stellen die Rohdaten des benutzerdefinierten Attributs dar.

 Wenn `ppBlob` die `pdwLen` und-Parameter auf einen NULL-Wert festgelegt sind, kann diese Methode verwendet werden, um zu bestimmen, ob das benutzerdefinierte Attribut nur vorhanden ist. Eine einfachere Alternative ist jedoch der Aufruf der [IsCustomAttributeDefined-Methode.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
