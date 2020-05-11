---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 465cc07b3ca75835afe0737fb22ba403acc4098b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734241"
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
[in, out] Gibt eine Zeichenfolge zurück, die den Namen der Sprache enthält, z. B. "C++".

`pguidLanguage`\
[in, out] Gibt die GUID für die Sprache des `guidCPPLang`Codekontexts zurück, z. B. .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mindestens einer der Parameter muss einen Wert ungleich NULL zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
