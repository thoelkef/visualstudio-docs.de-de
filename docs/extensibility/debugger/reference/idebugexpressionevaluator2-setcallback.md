---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729333"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Ermöglicht dem Ausdrucksevaluator (EE), die Rückrufschnittstelle anzugeben, die das Debuggermodul (DE) zum Lesen von Metrikeinstellungen verwendet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
[in] Schnittstelle, die für den Einstellungsrückruf verwendet werden soll.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Diese Methode stellt eine Schnittstelle zum Sitzungsdebug-Manager bereit, die ein Ausdrucksauswertungsdienst zum Lesen von Metrikeinstellungen verwenden kann. Es ist beim Remotedebugging nützlich, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] um Metriken auf dem Computer zu lesen.

## <a name="example"></a>Beispiel
Die folgenden Beispiele zeigen, wie Diese Methode für ein **CEE-Objekt** implementiert wird, das die [IDebugSettingsCallback2-Schnittstelle](../../../extensibility/debugger/reference/idebugsettingscallback2.md) verfügbar macht.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
