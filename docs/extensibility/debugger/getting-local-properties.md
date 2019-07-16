---
title: Abrufen von lokalen Eigenschaften | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c10cd5ebfe1efbf6657b9925c4c27cce33591524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338254"
---
# <a name="get-local-properties"></a>Abrufen von lokalen Eigenschaften
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio-Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zum Abrufen einer [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt, das Zugriff auf alle lokalen anzuzeigenden bietet die **"lokal"** Fenster. Visual Studio ruft dann [Weiter](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) zum Abrufen der Informationen für jede lokale angezeigt werden soll. In diesem Beispiel die Klasse `CEnumPropertyInfo` implementiert die `IEnumDebugPropertyInfo2` Schnittstelle.

Diese Implementierung der `IEnumDebugPropertyInfo2::Next` führt die folgenden Aufgaben:

1. Löscht das Array, an dem die Informationen gespeichert werden.

2. Aufrufe [Weiter](../../extensibility/debugger/reference/ienumdebugfields-next.md) für jede lokale, speichern Sie das zurückgegebene [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) im Array zurückgegeben werden. Die [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) Objekt wurde angegeben. wenn dies `CEnumPropertyInfo` Klasse instanziiert wurde.

## <a name="managed-code"></a>Verwalteter Code
Dieses Beispiel zeigt eine Implementierung von `IEnumDebugPropertyInfo2::EnumChildren` für eine Methode, die lokal in verwaltetem Code.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter code
 Dieses Beispiel zeigt eine Implementierung von `IEnumDebugPropertyInfo2::EnumChildren` für eine Methode "lokal" in nicht verwaltetem Code.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [Beispielimplementierung von lokalen Elementen](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Auflisten von lokalen Elementen](../../extensibility/debugger/enumerating-locals.md)
