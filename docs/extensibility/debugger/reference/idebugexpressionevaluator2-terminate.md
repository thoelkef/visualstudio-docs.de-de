---
title: IDebugExpressionEvaluator2::Beenden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Terminate
- IDebugExpressionEvaluator2::Terminate
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5460930cbcc528648c2a6c502ef7eb9acbe00d62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729156"
---
# <a name="idebugexpressionevaluator2terminate"></a>IDebugExpressionEvaluator2::Terminate
Beendet und bereinigt den Ausdrucksbewerter.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Terminate (
    void
);
```

```csharp
int Terminate ();
```

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Gibt den Ausdrucksbewerter an, wenn er bereinigt wird.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **ExpressionEvaluatorPackage-Objekt** implementiert wird, das die [IDebugExpressionEvaluator2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) verfügbar macht.

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)
{
    // scan the namespaces contained and delete
    EEExtensionMethodCache **ppChild = NULL;
    m_HashExtensionMethodCache.ResetHashIterator();
    while (ppChild = m_HashExtensionMethodCache.IterateHash())
    {
        delete *ppChild;
    }
    return VBEEImplicitVariables::Terminate();
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
