---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID-Methode"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
Listet die Member des Objekts auf.  
  
## Syntax  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### Parameter  
 `grfdex`  
 Bestimmt, das aus den Elementen sollen aufgelistet werden fest.  Diese kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|fdexEnumDefault|Anforderungen, dass das Objekt die Standardelemente auflistet.  Das Objekt ist zulässig, um aufzulisten ein Satz von Elementen.|  
|fdexEnumAll|Anforderungen, dass das Objekt alle Elemente auflistet.  Das Objekt ist zulässig, um aufzulisten ein Satz von Elementen.|  
  
 `id`  
 Identifiziert den aktuellen Member.  GetNextDispID ruft das Element in der Enumeration nach dieser ab.  Verwendung GetDispID oder eines vorherigen Aufruf GetNextDispID, zum Abrufen dieser Bezeichner.  Verwendet den DISPID\_STARTENUM\-Wert, erhält der erste Bezeichner des ersten Punkts.  
  
 `pid`  
 Adresse einer DISPID\-Variable, die den Bezeichner des nächsten Elements in der Enumeration empfängt.  
  
 Wenn ein Member von `DeleteMemberByName` oder `DeleteMemberByDispID` gelöscht wird, die `DISPID` Anforderungen, für `GetNextDispID` gültig.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Enumeration ist ausgeführt.|  
  
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
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)