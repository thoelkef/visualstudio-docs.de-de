---
title: Auflisten von "lokal" | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 036a5517f8605ed0052473a643a438534ffde277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enumerating-locals"></a>Auflisten von "lokal"
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn Visual Studio ist bereit zum Auffüllen der **"lokal"** Fenster, ruft er [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) auf die [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das von [ GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) (siehe [implementieren GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren` Gibt eine [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) Objekt.  
  
 Diese Implementierung der `IDebugProperty2::EnumChildren` führt die folgenden Aufgaben:  
  
1.  Stellt sicher, dass dies eine Methode darstellen.  
  
2.  Verwendet die `guidFilter` Argument, um zu bestimmen, welche Methode aufrufen, auf die [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Objekt. Wenn `guidFilter` entspricht:  
  
    1.  `guidFilterLocals`, rufen Sie [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) zum Abrufen einer [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) Objekt.  
  
    2.  `guidFilterArgs`, rufen Sie [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) zum Abrufen einer `IEnumDebugFields` Objekt.  
  
    3.  `guidFilterLocalsPlusArgs`, eine Enumeration, die die Ergebnisse kombiniert synthetisieren `IDebugMethodField::EnumLocals` und `IDebugMethodField::EnumArguments`. Diese Sprachsynthese wird dargestellt, von der Klasse `CEnumMethodField`.  
  
3.  Instanziiert eine Klasse (aufgerufen `CEnumPropertyInfo` in diesem Beispiel), implementiert die `IEnumDebugPropertyInfo2` Schnittstelle, und enthält die `IEnumDebugFields` Objekt.  
  
4.  Gibt die `IEnumDebugProperty2Info2` -Schnittstelle aus dem `CEnumPropertyInfo` Objekt.  
  
## <a name="managed-code"></a>Verwalteter Code  
 Dieses Beispiel zeigt eine Implementierung von `IDebugProperty2::EnumChildren` in verwaltetem Code.  
  
```csharp  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT EnumChildren (  
                uint                    dwFields,  
                uint                    radix,  
            ref Guid                    guidFilter,   
                ulong                   attribFilter,   
                string                  nameFilter,   
                uint                    timeout,  
            out IEnumDebugPropertyInfo2 properties)   
        {  
            properties = null;  
            IEnumDebugFields fields = null;  
  
            // If this field is a method...  
            if (0 != ((uint) fieldKind & (uint) FIELD_KIND.FIELD_TYPE_METHOD))  
            {  
                IDebugMethodField methodField = (IDebugMethodField) field;  
  
                // Enumerate parameters.  
                if (guidFilter == FilterGuids.guidFilterArgs)  
                {  
                    methodField.EnumParameters(out fields);    
                }  
                // Enumerate local variables.  
                else if (guidFilter == FilterGuids.guidFilterLocals)  
                {  
                    methodField.EnumLocals(address, out fields);    
                }  
                // Enumerate all local variables, including invisible compiler temps.  
                else if (guidFilter == FilterGuids.guidFilterAllLocals)  
                {  
                    methodField.EnumAllLocals(address, out fields);    
                }  
                // Enumerate "this", if any, and all parameters and local variables.  
                else if (guidFilter == FilterGuids.guidFilterLocalsPlusArgs)  
                {  
                    IDebugClassField fieldThis   = null;  
                    IEnumDebugFields parameters = null;  
                    IEnumDebugFields locals     = null;  
  
                    methodField.GetThis(out fieldThis);  
                    methodField.EnumParameters(out parameters);  
                    methodField.EnumLocals(address, out locals);  
  
                    CEnumMethodField enumMethodField =   
                        new CEnumMethodField(fieldThis, parameters, locals);  
                    fields = (IEnumDebugFields) enumMethodField;  
                }  
                // Enumerate only "this".  
                else if (guidFilter == FilterGuids.guidFilterThis)  
                {  
                    IDebugClassField fieldThis   = null;  
                    methodField.GetThis(out fieldThis);  
  
                    CEnumMethodField enumMethodField =   
                        new CEnumMethodField(fieldThis, null, null);  
                    fields = (IEnumDebugFields) enumMethodField;  
                }  
                else throw new COMException();// E_FAIL  
            }  
            // Wrap a property enumerator around the field enumerator.  
            CEnumPropertyInfo propertiesInfo =   
                new CEnumPropertyInfo(provider, address, binder, radix, fields,   
                 (DEBUGPROP_INFO_FLAGS) dwFields);  
  
            properties = (IEnumDebugPropertyInfo2) propertiesInfo;  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Nicht verwalteter Code  
 Dieses Beispiel zeigt eine Implementierung von `IDebugProperty2::EnumChildren` in nicht verwaltetem Code.  
  
```cpp  
STDMETHODIMP CFieldProperty::EnumChildren(   
        in DEBUGPROP_INFO_FLAGS        infoFlags,  
        in DWORD                       radix,  
        in REFGUID                     guidFilter,  
        in DBG_ATTRIB_FLAGS            attribFilter,  
        in LPCOLESTR                   pszNameFilter,  
        in DWORD                       timeout,  
        out IEnumDebugPropertyInfo2 ** ppchildren )  
{  
    if (ppchildren == NULL)  
        return E_INVALIDARG;  
    else  
        *ppchildren = 0;  
  
    //get enumeration  
    HRESULT hr;  
    IEnumDebugFields*     pfields    = NULL;  
  
    if (m_fieldKind & FIELD_TYPE_METHOD)  
    {  
        //-----------------------------------------------------  
        // A Method  
  
        IDebugMethodField*  pmethod    = NULL;  
  
        //enumerate the requested properties  
        hr = m_field->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod) );  
        if (FAILED(hr))  
            return hr;  
  
        if (guidFilter == guidFilterArgs)  
        {  
            hr = pmethod->EnumParameters( &pfields );    
        }  
        else if (guidFilter == guidFilterLocals)  
        {  
            hr = pmethod->EnumLocals( m_address, &pfields );  
        }  
        else if (guidFilter == guidFilterAllLocals)  
        {  
            hr = pmethod->EnumAllLocals( m_address, &pfields );  
        }  
        else if (guidFilter == guidFilterLocalsPlusArgs)  
        {  
            //we create a special enumerator for this  
            IDebugClassField* pfieldThis  = NULL;  
            IEnumDebugFields* pparameters = NULL;  
            IEnumDebugFields* plocals     = NULL;  
  
            pmethod->GetThis( &pfieldThis );  
            pmethod->EnumParameters( &pparameters );  
            pmethod->EnumLocals( m_address, &plocals );  
  
            CEnumMethodField* penumMethodField =  
                new CEnumMethodField( pfieldThis, pparameters, plocals );  
            if (pfieldThis != NULL)  
                pfieldThis->Release();  
            if (pparameters != NULL)  
                pparameters->Release();  
            if (plocals != NULL)  
                plocals->Release();  
            if (!penumMethodField)   
            {   
                hr = E_OUTOFMEMORY;  
            }  
            else  
            {  
                hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,  
                        reinterpret_cast<void**>(&pfields) );  
                penumMethodField->Release();  
            }  
        }  
        else if (guidFilter == guidFilterThis )  
        {  
            IDebugClassField* pfieldThis  = NULL;  
  
            hr = pmethod->GetThis( &pfieldThis );  
            if (SUCCEEDED(hr))  
            {  
                CEnumMethodField* penumMethodField =  
                    new CEnumMethodField( pfieldThis, NULL, NULL );  
                pfieldThis->Release();  
                if (!penumMethodField)   
                {  
                    hr = E_OUTOFMEMORY;  
                }  
                else  
                {  
                    hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,  
                        reinterpret_cast<void**>(&pfields) );  
                    penumMethodField->Release();  
                }  
            }  
        }  
        else  
        {  
            hr = E_FAIL;  
        }  
  
        pmethod->Release();  
        if (hr != S_OK)  
            return hr;  
    }  
  
    //create a property info enumeration around the field enumerator  
    CEnumPropertyInfo* pproperties =  
        new CEnumPropertyInfo( m_provider, m_address, m_binder,   
                               radix, pfields, infoFlags );  
    if (pfields != NULL)  
        pfields->Release();  
    if (pproperties == NULL)  
        return E_OUTOFMEMORY;  
  
    hr = pproperties->QueryInterface( IID_IEnumDebugPropertyInfo2,  
        reinterpret_cast<void**>(ppchildren) );  
    pproperties->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Beispielimplementierung von "lokal"](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Implementieren von GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)   
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)