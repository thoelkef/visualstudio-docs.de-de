---
title: IPerPropertyBrowsing2::GetDisplayString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be88a76ce22dfd863e680fcc1a6794065ecaf76f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836878"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Ruft eine Zeichenfolge zum Anzeigen von Typen, die nicht grundsätzlich angezeigt werden. des zurückgegebenen Texts ist ein Name, Beschreibung der Eigenschaft und kann in der Benutzeroberfläche des Aufrufers angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Der Dispatchbezeichner der Eigenschaft, deren Anzeigename angefordert wird.  
  
 `pBstr`  
 [out] Zeiger auf die `BSTR` mit dem Anzeigenamen für die identifizierte Eigenschaft `dispID`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebene Zeichenfolge ist kein zulässiger Wert der Eigenschaft. Es ist nur eine Zeichenfolgenanzeige der Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)