---
title: IDispatchEx::GetMemberProperties | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f607e06fe3c898a6839c0bbd2d51edee1f0ffb2c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160731"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Ruft ein Element der Eigenschaften ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` die Dispatch-ID abgerufen.  
  
 `grfdexFetch`  
 Bestimmt, welche Eigenschaften abgerufen. Dies liegt möglicherweise eine Kombination der Werte unter `pgrfdex` bzw. eine Kombination der folgenden Werte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|grfdexPropCanAll|Kombiniert FdexPropCanGet, FdexPropCanPut, FdexPropCanPutRef, FdexPropCanCall, FdexPropCanConstruct und FdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombiniert FdexPropCannotGet, FdexPropCannotPut, FdexPropCannotPutRef, FdexPropCannotCall, FdexPropCannotConstruct und FdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects kombiniert FdexPropDynamicType.|  
|grfdexPropAll|Kombiniert GrfdexPropCanAll, GrfdexPropCannotAll und GrfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresse von einem `DWORD` , empfängt die angeforderten Eigenschaften. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexPropCanGet|Das Element kann mit DISPATCH_PROPERTYGET abgerufen werden.|  
|fdexPropCannotGet|Das Element kann nicht mithilfe von DISPATCH_PROPERTYGET abgerufen werden.|  
|fdexPropCanPut|Das Element kann mit DISPATCH_PROPERTYPUT festgelegt werden.|  
|fdexPropCannotPut|Das Element kann nicht mithilfe von DISPATCH_PROPERTYPUT festgelegt werden.|  
|fdexPropCanPutRef|Das Element kann mit DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|fdexPropCannotPutRef|Das Element kann nicht mithilfe von DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|fdexPropNoSideEffects|Das Element ist nicht keine Nebeneffekte haben. Ein Debugger kann z. B. sicher Get/Set/Aufruf dieses Members ohne Ändern des Status des Skripts, die gedebuggt wird.|  
|fdexPropDynamicType|Das Element ist dynamisch und kann während der Lebensdauer des Objekts ändern.|  
|fdexPropCanCall|Das Element kann als eine Methode mithilfe von DISPATCH_METHOD aufgerufen werden.|  
|fdexPropCannotCall|Das Element kann nicht als eine Methode mithilfe von DISPATCH_METHOD aufgerufen werden.|  
|fdexPropCanConstruct|Das Element kann als mit DISPATCH_CONSTRUCT Konstruktor aufgerufen werden.|  
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
  
```cpp
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