---
title: IDispatchEx::GetMemberName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberName
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberName method
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 155c8db6e772460ae8ad4e8b5a70ae5e67b49ec1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000878"
---
# <a name="idispatchexgetmembername"></a>IDispatchEx::GetMemberName
Ruft den Namen eines Members ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` die Dispatch-ID abgerufen.  
  
 `pbstrName`  
 Adresse von einem `BSTR` , der den Namen des Members empfängt. Die aufrufende Anwendung ist verantwortlich für das Freigeben dieses Werts.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|`DISP_E_UNKNOWNNAME`|Der Name wurde nicht bekannt.|  
  
## <a name="example"></a>Beispiel  
  
```cpp
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
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)