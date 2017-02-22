---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "IDebugSymbolProvider-Schnittstelle"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Anbieter Symbol, der Symbole und Typen bereitstellt und gibt sie als Felder zurück.  
  
## Syntax  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter muss diese Schnittstelle implementieren, um Typinformationen und Symbol an einen Ausdrucksauswertung angeben.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, indem `CoCreateInstance`\-Funktion COM \(für nicht verwalteten Anbieter Symbol\) oder indem die entsprechende verwaltete Codeassembly lädt und Hersteller des Symbols basierend auf den Informationen in dieser Assembly instanziiert.  Das Debugmodul instanziiert den Anbieter Symbol, um in Abstimmung mit dem Ausdrucksauswertung zu arbeiten.  Weitere Informationen finden Sie im Beispiel für einen Ansatz zum Instanziieren dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugSymbolProvider`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|`Initialize`|Veraltet.  Nicht verwenden.|  
|`Uninitialize`|Veraltet.  Nicht verwenden.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ruft das Rechteck ab, das die Debuginformationen Adresse enthält.|  
|`GetField`|Veraltet.  Nicht verwenden.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Ordnet eine Position des Dokuments in ein Array von Adressen zu.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Ordnet den Dokumentenkontext in ein Array von Adressen zu.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Ordnet eine Adresse in den Dokumentenkontext.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ruft die Sprache ab, die verwendet wird, um den Code an der Adresse Debuggen kompilieren.|  
|`GetGlobalContainer`|Veraltet.  Nicht verwenden.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ruft das Rechteck ab, das einen vollqualifizierten Methodennamen darstellt.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Klassenfeld Ruft den Typ ab, der einen vollqualifizierten Klassennamen darstellt.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Erstellt einen Enumerator für die Namespaces Debuggen, die mit der Adresse zugeordnet sind.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Ordnet einen Symbolnamen auf ein Symbol für den Typ.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ruft die Adresse ab, die die ein angegebenes debuggen Adresse in einer Methode erfolgreich ausgeführt wurde.|  
  
## Hinweise  
 Diese Schnittstelle weist Adressen von Positionen in Dokumenten und umgekehrt.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
 Dieses Beispiel zeigt, wie Sie den Anbieter Symbol angegeben werden, instanziiert ein GUID \(Debug\) \- Modul muss diesen Wert kennen.  
  
```cpp#  
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
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)