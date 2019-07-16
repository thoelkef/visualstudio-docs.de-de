---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08138fcd67e7d4fd5115ac13fe1b8348f76245d8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339012"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ruft die Sprachinformationen für diesen Codekontext ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parameter
`pbstrLanguage`\
[in, out] Gibt eine Zeichenfolge mit dem Namen der Sprache, z. B. "C++."

`pguidLanguage`\
[in, out] Beispielsweise gibt die GUID für die Sprache der Codekontext `guidCPPLang`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Mindestens einer der Parameter muss einen Wert ungleich Null zurückgeben.

## <a name="see-also"></a>Siehe auch
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)