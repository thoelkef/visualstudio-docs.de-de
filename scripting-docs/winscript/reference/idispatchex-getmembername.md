---
title: "IDispatchEx::GetMemberName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberName-Methode"
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberName
Ruft den Namen eines Members ab.  
  
## Syntax  
  
```  
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### Parameter  
 `id`  
 Bezeichnet den Member.  Verwendung `GetDispID` oder `GetNextDispID`, in der Dispatchbezeichner.  
  
 `pbstrName`  
 Adresse von `BSTR`, die den Namen des Members empfängt.  Die Anwendung ist für die Freigabe dieses Werts zuständig.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_UNKNOWNNAME`|Der Name ist nicht bekannt.|  
  
## Beispiel  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
   SysFreeString(bstrName);  
   hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)