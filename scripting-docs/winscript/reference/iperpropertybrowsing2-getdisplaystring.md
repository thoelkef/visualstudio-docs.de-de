---
title: 'IPerPropertyBrowsing2:: GetDisplayString | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571448"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Ruft eine Zeichenfolge zum Anzeigen von Typen ab, die nicht grundsätzlich sichtbar sind. der zurückgegebene Text ist ein Name, der die Eigenschaft beschreibt und in der Benutzeroberfläche des Aufrufers angezeigt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 in Dispatchbezeichner der Eigenschaft, deren Anzeige Name angefordert wird.  
  
 `pBstr`  
 vorgenommen Ein Zeiger auf die `BSTR`, die den anzeigen Amen für die durch `dispID` identifizierte Eigenschaft enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebene Zeichenfolge ist kein gültiger Wert der-Eigenschaft. Es handelt sich lediglich um eine Zeichen folgen Anzeige der-Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)