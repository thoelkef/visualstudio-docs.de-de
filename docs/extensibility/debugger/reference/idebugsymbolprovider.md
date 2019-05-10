---
title: IDebugSymbolProvider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98bd86cd219ec2604816e290f75e02d1f9530a53
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457631"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Diese Schnittstelle stellt einen symbolanbieter, der Symbole und Typen, die sie als Felder zurückgegeben werden bereitstellt.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein symbolanbieter muss diese Schnittstelle zum Angeben von Symbol, und geben Sie Informationen zu einer ausdrucksauswertung implementieren.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Diese Schnittstelle wird abrufen, mithilfe von COM `CoCreateInstance` -Funktion (für nicht verwaltete Symbol-Anbieter) oder durch Laden der entsprechenden verwalteten Codeassembly und Instanziieren des Symbol-Anbieters, die anhand der Informationen in dieser Assembly gefundenen. Die Debug-Engine instanziiert die symbolanbieter funktioniert in Kombination mit der ausdrucksauswertung. Siehe das Beispiel einen Ansatz für die diese Schnittstelle zu instanziieren.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDebugSymbolProvider`.

|Methode|Beschreibung|
|------------|-----------------|
|`Initialize`|Veraltet. Nicht verwenden.|
|`Uninitialize`|Veraltet. Nicht verwenden.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ruft das Feld, das die debugadresse enthält.|
|`GetField`|Veraltet. Nicht verwenden.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Ordnet eine Dokumentposition in ein Array von Debug-Adressen.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Ordnet einem Dokumentkontext in ein Array von Debug-Adressen an.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Ordnet eine debugadresse in einen Dokumentkontext.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ruft die Sprache zum Kompilieren des Codes an der debugadresse ab.|
|`GetGlobalContainer`|Veraltet. Nicht verwenden.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ruft das Feld, das einen vollqualifizierten Methodennamen darstellt.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ruft den Klassentyp-Feld, das einen vollqualifizierten Klassennamen darstellt.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Erstellt einen Enumerator für Namespaces, die mit der debugadresse verknüpft.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Ordnet einen Symbolnamen ein Symboltyp.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ruft die debugadresse, die eine angegebenen Adresse in einer Methode folgt.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle ordnet Dokumentpositionen in Debug-Adressen und umgekehrt.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie den symbolanbieter zu instanziieren, wenn seine GUID (eine Debug-Engine muss dieser Wert bekannt).

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

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
