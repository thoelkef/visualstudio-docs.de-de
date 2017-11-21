---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Ermöglicht dem Aufrufer ein Listenfeld mit einem gezählten Array von Zeigern Zeichenfolge füllen Sie die möglichen Werte für diese Eigenschaft darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Dispatch-ID der Eigenschaft für die der Aufrufer die Zeichenfolgenliste anfordert.  
  
 `pCaStrings`  
 [out] Ein Zeiger auf eine, zählbare, das vom Aufrufer zugewiesene Arraystruktur, die Elementanzahl und die Adresse ein Methode reserviertes Array von Zeigern Zeichenfolge enthält. Wenn die Methode fehlschlägt, wird kein Speicherplatz belegt, und den Inhalt der Struktur ist nicht definiert.  
  
 `pCaCookies`  
 [out] Zeiger auf die vom Aufrufer reservierten, zählbare Arraystruktur, die die Elementanzahl und die Adresse einer Methode reserviertes Array von DWORDs enthält. Wenn die Methode fehlschlägt, wird kein Speicherplatz belegt, und den Inhalt der Struktur ist nicht definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)