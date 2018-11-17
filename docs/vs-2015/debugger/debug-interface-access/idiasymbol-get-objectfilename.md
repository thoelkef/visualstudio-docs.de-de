---
title: IDiaSymbol::get_objectFileName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4b74c460ffc01f0abcb737dc7f727a3d5d3406a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729876"
---
# <a name="idiasymbolgetobjectfilename"></a>IDiaSymbol::get_objectFileName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ab, der Name der Objektdatei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_objectFilename(   
   BSTR *pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `BSTR` , enthält der Name der Objektdatei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



