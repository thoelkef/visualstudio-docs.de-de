---
title: "Implementieren von GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMethodProperty-Methode"
  - "IDebugExpressionEvaluator2-Eigenschaft"
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Implementieren von GetMethodProperty
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio ruft das Debuggen Modul \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), wodurch wiederum aufgerufen [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) zum Abrufen von Informationen über die aktuelle Methode auf dem Stapelrahmen.  
  
 Diese Implementierung der `IDebugExpressionEvaluator::GetMethodProperty` führt die folgenden Aufgaben:  
  
1.  Aufrufe [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), übergibt die [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Objekt. Gibt der Symbol\-Anbieter \(SP\) eine [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) die Methode mit der angegebenen Adresse darstellt.  
  
2.  Ruft die [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) aus der `IDebugContainerField`.  
  
3.  Instanziiert eine Klasse \(aufgerufen `CFieldProperty` in diesem Beispiel\), implementiert der [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle und enthält die `IDebugMethodField` Objekt zurückgegeben wird, von SP  
  
4.  Gibt die `IDebugProperty2` \-Schnittstelle aus der `CFieldProperty` Objekt.  
  
## Verwalteter Code  
 Dieses Beispiel zeigt eine Implementierung von `IDebugExpressionEvaluator::GetMethodProperty` in verwaltetem Code.  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## Nicht verwalteter Code  
 Dieses Beispiel zeigt eine Implementierung von `IDebugExpressionEvaluator::GetMethodProperty` in nicht verwaltetem Code.  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## Siehe auch  
 [Beispielimplementierung von lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md)