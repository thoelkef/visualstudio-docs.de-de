---
title: IDebugDocumentContext2::GetLanguageInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugDocumentContext2::GetLanguageInfo
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2895d943196f29f39d1abd38415be7ad374f0012
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450217"
---
# <a name="idebugdocumentcontext2getlanguageinfo"></a>IDebugDocumentContext2::GetLanguageInfo
Ruft die diesem Dokumentenkontext zugeordnete Sprache ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguageInfo(
    BSTR* pbstrLanguage,
    GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo(
    out string pbstrLanguage,
    out Guid   pguidLanguage
);
```

#### <a name="parameters"></a>Parameter
`pbstrLanguage`  
[out] Gibt den Namen der Sprache, die den Code in diesem Dokumentenkontext implementiert.

`pguidLanguage`  
[out] Gibt die GUID der Sprache, die den Code in diesem Dokumentenkontext implementiert. Beispielsweise `guidVBScriptLang` oder `guidCPPLang`. Diese GUID ist nicht beschränkt auf die Sprachen, die vom [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CDebugContext` -Objekt, das macht die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle.

```cpp
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)
{
    HRESULT hr;

    // Check for a valid language argument pointers.
    if (pbstrLanguage && pguidLanguage)
    {
        *pguidLanguage = GUID_NULL;
        *pbstrLanguage = SysAllocString(L"Batch File");
        if (*pbstrLanguage)
        {
            *pguidLanguage = guidBatLang;
            hr = S_OK;
        }
        else
        {
            hr = E_OUTOFMEMORY;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
