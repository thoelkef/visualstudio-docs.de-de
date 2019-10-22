---
title: 'IPerPropertyBrowsing2:: getpredefinedstrings | Microsoft-Dokumentation'
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
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576772"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Ermöglicht dem Aufrufer, ein Listenfeld mit einem gezählten Array von Zeichen folgen Zeigern auszufüllen, die mögliche Werte für diese Eigenschaft darstellen.  
  
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
 in Dispatchbezeichner der Eigenschaft, für die der Aufrufer die Zeichen folgen Liste anfordert.  
  
 `pCaStrings`  
 vorgenommen Zeiger auf eine vom Aufrufer zugeordnete Array Struktur, die die Element Anzahl und die Adresse eines von der Methode zugeordneten Arrays von Zeichen folgen Zeigern enthält. Wenn die Methode fehlschlägt, wird kein Arbeitsspeicher zugeordnet, und der Inhalt der Struktur ist nicht definiert.  
  
 `pCaCookies`  
 vorgenommen Ein Zeiger auf die vom Aufrufer zugeordnete Array Struktur, die die Element Anzahl und die Adresse eines von der Methode zugeordneten DWords-Arrays enthält. Wenn die Methode fehlschlägt, wird kein Arbeitsspeicher zugeordnet, und der Inhalt der Struktur ist nicht definiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine gültige `HRESULT` zurück, die in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)