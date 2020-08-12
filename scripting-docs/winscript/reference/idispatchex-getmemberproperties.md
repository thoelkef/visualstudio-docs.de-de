---
title: 'IDispatchEx:: getmembership Properties | Microsoft-Dokumentation'
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
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144547"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Ruft die Eigenschaften eines Members ab.  
  
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
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` , um den Dispatchbezeichner abzurufen.  
  
 `grfdexFetch`  
 Bestimmt, welche Eigenschaften abgerufen werden sollen. Dabei kann es sich um eine Kombination der Werte handeln, die unter `pgrfdex` und/oder einer Kombination der folgenden Werte aufgeführt sind:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|GRF-proppropcanall|Kombiniert fdexpropcanget, fdexpropcanput, fdexpropcanputref, fdexpropcancall, fdexpropcanconstruct und fdexpropcansourceevents.|  
|GRF-propcannotall|Kombiniert fdexpropcannotget, fdexpropcannotput, fdexpropcannotputref, fdexpropcannotcall, fdexpropcannotconstruct und fdexpropcannotsourceevents.|  
|GRF-propextraall|Kombiniert ' f ' propnosideeffects ' und ' ' ' ' '.|  
|GRF-proppropall|Kombiniert "GRF" propcanall, "GRF" propcannotall und "GRF dexpropextraall".|  
  
 `pgrfdex`  
 Adresse eines `DWORD` , das die angeforderten Eigenschaften empfängt. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|' f ' propcanget|Der Member kann mit DISPATCH_PROPERTYGET abgerufen werden.|  
|' f ' propcannotget|Der Member kann nicht mit DISPATCH_PROPERTYGET abgerufen werden.|  
|' f ' propcanput|Der Member kann mit DISPATCH_PROPERTYPUT festgelegt werden.|  
|' f ' propcannotput|Der Member kann nicht mit DISPATCH_PROPERTYPUT festgelegt werden.|  
|' f ' propcanputref|Der Member kann mit DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|' f ' propcannotputref|Der Member kann nicht mit DISPATCH_PROPERTYPUTREF festgelegt werden.|  
|"f" propnosideeffects|Der Member hat keine Nebeneffekte. Ein Debugger kann diesen Member z. b. sicher abrufen, festlegen/abrufen, ohne den Status des Skripts zu ändern, das gedebuggt wird.|  
|' f ' propdynamictype|Der-Member ist dynamisch und kann sich während der Lebensdauer des-Objekts ändern.|  
|fdexpropcancall|Der Member kann mithilfe von DISPATCH_METHOD als Methode aufgerufen werden.|  
|fdexpropcannotcall|Der Member kann nicht als Methode mithilfe von DISPATCH_METHOD aufgerufen werden.|  
|' f ' propcanconstruct|Der Member kann mit DISPATCH_CONSTRUCT als Konstruktor aufgerufen werden.|  
|' f ' propcannotconstruct|Der Member kann nicht als Konstruktor mit DISPATCH_CONSTRUCT aufgerufen werden.|  
|' f ' propcansourceevents|Der Member kann Ereignisse auslösen.|  
|' f ' propcannotsourceevents|Der Member kann keine Ereignisse auslösen.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|
|-|-|  
|`S_OK`|Erfolg.|  
|`DISP_E_UNKNOWNNAME`|Der Name war nicht bekannt.|  
  
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
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)