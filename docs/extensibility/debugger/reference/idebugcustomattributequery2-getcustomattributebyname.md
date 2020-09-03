---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732560"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ruft die benutzerdefinierten Attribute Bytes ab, wenn der Name des benutzerdefinierten Attributs angegeben ist.

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
in Eine Zeichenfolge mit dem Namen des benutzerdefinierten Attributs, nach dem gesucht werden soll.

`ppBlob`\
[in, out] Ein Array, das mit den benutzerdefinierten Attribut Bytes gefüllt ist.

`pdwLen`\
[in, out] Gibt die maximale Anzahl von Bytes an, die im Array zurückgegeben werden sollen, `ppBlob` und gibt die Anzahl der Bytes zurück, die tatsächlich in das Array geschrieben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben oder S_FALSE zurückgegeben, wenn das benutzerdefinierte Attribut nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Legen Sie den- `ppBlob` Parameter auf einen NULL-Wert fest, um die Anzahl der verfügbaren Bytes zurückzugeben. Weisen Sie dann ein Array zu, und übergeben Sie das Array für den `ppBlob` Parameter.

 Die Attribut Bytes stellen die Rohdaten des benutzerdefinierten Attributs dar.

 Wenn der `ppBlob` -Parameter und der- `pdwLen` Parameter auf einen NULL-Wert festgelegt sind, kann mit dieser Methode ermittelt werden, ob das benutzerdefinierte Attribut nur vorhanden ist. Eine einfachere Alternative besteht jedoch darin, die [iscustomattributedefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) -Methode aufzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
