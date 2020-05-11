---
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719167"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Diese Schnittstelle stellt einen Symbolanbieter dar, der Symbole und Typen bereitstellt und sie als Felder zurückgibt.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein Symbolanbieter muss diese Schnittstelle implementieren, um Symbol- und Typinformationen an einen Ausdrucksevaluator zu übermitteln.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Diese Schnittstelle wird mithilfe der `CoCreateInstance` COM-Funktion (für nicht verwaltete Symbolanbieter) oder durch Laden der entsprechenden verwalteten Codeassembly und Instanziieren des Symbolanbieters basierend auf den in dieser Assembly gefundenen Informationen abgerufen. Das Debugmodul instanziiert den Symbolanbieter, um in Abstimmung mit dem Ausdrucksevaluator zu arbeiten. Siehe Beispiel für einen Ansatz zum Instanziieren dieser Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt `IDebugSymbolProvider`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|`Initialize`|Veraltet. Darf nicht verwendet werden.|
|`Uninitialize`|Veraltet. Darf nicht verwendet werden.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ruft das Feld ab, das die Debugadresse enthält.|
|`GetField`|Veraltet. Darf nicht verwendet werden.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Ordnet eine Dokumentposition einem Array von Debugadressen zu.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Ordnet einen Dokumentkontext einem Array von Debugadressen zu.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Ordnet eine Debugadresse einem Dokumentkontext zu.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ruft die Sprache ab, die zum Kompilieren des Codes an der Debugadresse verwendet wird.|
|`GetGlobalContainer`|Veraltet. Darf nicht verwendet werden.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ruft das Feld ab, das einen vollqualifizierten Methodennamen darstellt.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ruft den Klassenfeldtyp ab, der einen vollqualifizierten Klassennamen darstellt.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Erstellt einen Enumerator für Namespaces, die der Debugadresse zugeordnet sind.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Ordnet einem Symboltyp einen Symbolnamen zu.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ruft die Debugadresse ab, die einer bestimmten Debugadresse in einer Methode folgt.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle ordnet Dokumentpositionen Debugadressen zu und umgekehrt.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie der Symbolanbieter angesichts seiner GUID instanziiert wird (ein Debugmodul muss diesen Wert kennen).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
