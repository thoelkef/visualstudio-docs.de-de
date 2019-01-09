---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3bec9643a89d40a7b1e37d019d4211bd7167ee65
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088607"
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