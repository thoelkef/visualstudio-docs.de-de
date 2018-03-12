---
title: IDispatchEx::GetMemberProperties | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Ruft die Eigenschaften eines Elements ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` die Dispatch-ID abrufen.  
  
 `grfdexFetch`  
 Bestimmt, welche Eigenschaften abgerufen. Dies kann eine Kombination der Werte, die unter aufgeführten `pgrfdex` und/oder eine Kombination der folgenden Werte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|grfdexPropCanAll|Kombiniert FdexPropCanGet, FdexPropCanPut, FdexPropCanPutRef, FdexPropCanCall, FdexPropCanConstruct und FdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombiniert FdexPropCannotGet, FdexPropCannotPut, FdexPropCannotPutRef, FdexPropCannotCall, FdexPropCannotConstruct und FdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects und FdexPropDynamicType kombiniert.|  
|grfdexPropAll|Kombiniert GrfdexPropCanAll, GrfdexPropCannotAll und GrfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresse der einen `DWORD` , empfängt die angeforderten Eigenschaften. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexPropCanGet|Das Element kann mithilfe von DISPATCH_PROPERTYGET abgerufen werden.|  
|fdexPropCannotGet|Das Element kann nicht mithilfe von DISPATCH_PROPERTYGET abgerufen werden.|  
|fdexPropCanPut|Das Element kann mit DISPATCH_PROPERTYPUT festgelegt werden.|  
|fdexPropCannotPut|Das Element kann nicht mit DISPATCH_PROPERTYPUT festgelegt werden.|  
|fdexPropCanPutRef|Das Element kann mit DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|fdexPropCannotPutRef|Das Element kann nicht mit DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|fdexPropNoSideEffects|Das Element ist nicht keine Nebeneffekte haben. Z. B. ein Debugger sicher Get/Set/Aufruf bei diesem Member ohne Änderung des Zustands des Skripts, der debuggt wird.|  
|fdexPropDynamicType|Das Element ist dynamisch und kann während der Lebensdauer des Objekts ändern.|  
|fdexPropCanCall|Das Element kann als eine Methode mit DISPATCH_METHOD aufgerufen werden.|  
|fdexPropCannotCall|Das Element kann nicht als eine Methode mit DISPATCH_METHOD aufgerufen werden.|  
|fdexPropCanConstruct|Das Element kann als einen Konstruktor mit DISPATCH_CONSTRUCT aufgerufen werden.|  
|fdexPropCannotConstruct|Das Element kann nicht als einen Konstruktor mit DISPATCH_CONSTRUCT aufgerufen werden.|  
|fdexPropCanSourceEvents|Das Element kann Ereignisse ausgelöst werden.|  
|fdexPropCannotSourceEvents|Das Element kann keine Ereignisse auslösen.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_UNKNOWNNAME`|Der Name wurde nicht bekannt.|  
  
## <a name="example"></a>Beispiel  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)