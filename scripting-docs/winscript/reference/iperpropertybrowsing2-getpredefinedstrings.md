---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a5f71ba91c65a8d99d831c777fc47fe9233fc18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944853"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Ermöglicht dem Aufrufer ein Listenfeld, das mit der ein gezähltes Array von Zeichenfolgenzeiger zu füllen, die möglichen Werte für diese Eigenschaft darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Dispatch-ID der Eigenschaft, die für die der Aufrufer die Zeichenfolgenliste anfordert.  
  
 `pCaStrings`  
 [out] Zeiger auf eine vom Aufrufer reservierte, gezähltes Array-Struktur, die die Elementanzahl und die Adresse eines Arrays-Methode zugeordnete Zeichenfolge Zeiger enthält. Wenn die Methode fehlschlägt, wird kein Arbeitsspeicher belegt und der Inhalt der Struktur ist nicht definiert.  
  
 `pCaCookies`  
 [out] Zeiger auf die vom Aufrufer reservierte, gezähltes Array-Struktur, die die Elementanzahl und die Adresse von einer Methode reserviertes Array von DWORDs enthält. Wenn die Methode fehlschlägt, wird kein Arbeitsspeicher belegt und der Inhalt der Struktur ist nicht definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)