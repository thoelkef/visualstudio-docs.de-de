---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties-Methode"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
Ruft die Eigenschaften eines Members ab.  
  
## Syntax  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### Parameter  
 `id`  
 Bezeichnet den Member.  Verwendung `GetDispID` oder `GetNextDispID`, in der Dispatchbezeichner.  
  
 `grfdexFetch`  
 Bestimmt, das Eigenschaften abzurufen.  Diese kann eine Kombination der Werte, die unter aufgeführt sind `pgrfdex` und\/oder eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|grfdexPropCanAll|Kombiniert fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct und fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombiniert fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct und fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Kombiniert fdexPropNoSideEffects und fdexPropDynamicType.|  
|grfdexPropAll|Kombiniert grfdexPropCanAll, grfdexPropCannotAll und grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresse von `DWORD`, die die angeforderten Eigenschaften empfängt.  Diese kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|fdexPropCanGet|Der Member kann mithilfe DISPATCH\_PROPERTYGET abgerufen werden.|  
|fdexPropCannotGet|Der Member kann nicht mit DISPATCH\_PROPERTYGET abgerufen werden.|  
|fdexPropCanPut|Der Member kann mithilfe DISPATCH\_PROPERTYPUT festgelegt werden.|  
|fdexPropCannotPut|Der Member kann nicht mit DISPATCH\_PROPERTYPUT festgelegt werden.|  
|fdexPropCanPutRef|Der Member kann mithilfe DISPATCH\_PROPERTYPUTREF festgelegt werden.|  
|fdexPropCannotPutRef|Der Member kann nicht mit DISPATCH\_PROPERTYPUTREF festgelegt werden.|  
|fdexPropNoSideEffects|Der Member hat keine Nebeneffekte.  Beispielsweise kann ein Debugger, sicher\/Satz\/Aufruf dieser Member abzurufen, ohne den Zustand des Skripts zu ändern, das gedebuggt wurde.|  
|fdexPropDynamicType|Der Member ist dynamisch und kann während der Lebensdauer des Objekts ändern.|  
|fdexPropCanCall|Der Member kann als Methode mithilfe DISPATCH\_METHOD aufgerufen werden.|  
|fdexPropCannotCall|Der Member kann nicht als Methode mithilfe DISPATCH\_METHOD aufgerufen werden.|  
|fdexPropCanConstruct|Der Member kann als Konstruktor mit DISPATCH\_CONSTRUCT aufgerufen werden.|  
|fdexPropCannotConstruct|Der Member kann nicht als Konstruktor mit DISPATCH\_CONSTRUCT aufgerufen werden.|  
|fdexPropCanSourceEvents|Der Member kann Ereignisse auslösen.|  
|fdexPropCannotSourceEvents|Der Member kann keine Ereignisse auslösen.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_UNKNOWNNAME`|Der Name ist nicht bekannt.|  
  
## Beispiel  
  
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
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)