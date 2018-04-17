---
title: IDebugSymbolProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de77e30f0e9f52af10eef1757048a078d6d4a583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Diese Schnittstelle stellt einen Symbol-Anbieter, der Symbole und Typen, deren Rückgabe als Felder bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol muss vom Anbieter implementiert diese Schnittstelle zum Angeben von Symbol und eine ausdrucksauswertung Typinformationen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, mithilfe von COM `CoCreateInstance` -Funktion (für nicht verwalteten Symbol-Anbieter) oder durch Laden der entsprechenden verwalteten Codeassembly und instanziieren den Symbol-Anbieter, die anhand der Informationen in dieser Assembly gefunden. Das Debugmodul instanziiert den Symbol-Anbieter funktioniert in Kombination mit der ausdrucksauswertung. Siehe das Beispiel für eine Möglichkeit, diese Schnittstelle zu instanziieren.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugSymbolProvider`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|`Initialize`|Veraltet. Nicht verwenden.|  
|`Uninitialize`|Veraltet. Nicht verwenden.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ruft das Feld, das die Debug-Adresse enthält.|  
|`GetField`|Veraltet. Nicht verwenden.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Ordnet eine Dokumentposition in ein Array der Debug-Adressen an.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Ordnet einen Dokumentenkontext in ein Array von Adressen Debuggen.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Eine Debug-Adresse in einem Dokumentenkontext zugeordnet.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ruft die Sprache zum Kompilieren des Codes bei der Debug-Adresse verwendet.|  
|`GetGlobalContainer`|Veraltet. Nicht verwenden.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ruft das Feld, das einen Namen für vollständig qualifizierte Methode darstellt.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ruft ab, der Typ des Felds Klasse, die einen vollqualifizierten Klassennamen darstellt.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Erstellt einen Enumerator für Namespaces, die die Debug-Adresse zugeordnet.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Ordnet einen Symbolnamen ein Symboltyp.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ruft die Debug-Adresse, die eine angegebenen Adresse in einer Methode folgt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ordnet Dokumentpositionen in Debug-Adressen und umgekehrt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie den Symbol-Anbieter instanziieren, erhält seine GUID (ein Debugging-Modul muss dieser Wert bekannt).  
  
```cpp  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)