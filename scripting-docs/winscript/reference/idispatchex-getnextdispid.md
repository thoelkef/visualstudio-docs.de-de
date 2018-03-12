---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Listet die Member des Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `grfdex`  
 Bestimmt, welche Gruppe von Elementen sind, aufgelistet werden sollen. Dies kann eine Kombination der folgenden Werte sein:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|fdexEnumDefault|Fordert an, dass das Objekt die Standardelemente zählt. Das Objekt ist zulässig, einen beliebigen Satz von Elementen aufgelistet werden.|  
|fdexEnumAll|Fordert an, dass das Objekt alle Elemente zählt. Das Objekt ist zulässig, einen beliebigen Satz von Elementen aufgelistet werden.|  
  
 `id`  
 Gibt das aktuelle Element. GetNextDispID Ruft das Element in der Enumeration nach diesem ab. Verwendet GetDispID oder einem vorherigen Aufruf GetNextDispID, um diesen Bezeichner abzurufen. Verwendet zum Abrufen des ersten Bezeichners des ersten Elements der DISPID_STARTENUM-Wert.  
  
 `pid`  
 Adresse des einen DISPID-Variable, die den Bezeichner des nächsten Elements in der Enumeration empfängt.  
  
 Wenn ein Element, indem gelöscht wird `DeleteMemberByName` oder `DeleteMemberByDispID`, `DISPID` für gültig bleiben muss, `GetNextDispID`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`S_FALSE`|Enumeration erfolgt.|  
  
## <a name="example"></a>Beispiel  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)