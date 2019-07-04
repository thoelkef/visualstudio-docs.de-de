---
title: IDebugStackFrame2::GetLanguageInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0318f99d234309093717c9603ec1153e71d6d7f3
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559695"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Ruft die Sprache, die diesen Stapelrahmen zugeordnet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parameter

`pbstrLanguage`\
[out] Gibt den Namen der Sprache, die die Methode, die diesen Stapelrahmen zugeordnet implementiert.

`pguidLanguage`\
[out] Gibt die `GUID` der Sprache. Für die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Sprachen, z. B. die folgenden zurückgegeben werden können:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Rückgabewert

 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
