---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 95f535bd314ec998c83ec9c02aab2190646f3c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Ruft Zeichenfolgennamen für entsprechende angegebenen Eigenschaftsbezeichner.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpropid`  
 [in] Anzahl der Eigenschafts-Ids in `rgpropid`.  
  
 `rgpropid`  
 [in] Array von Eigenschaften-Ids für die die Namen abgerufen (`PROPID` ist definiert in WTypes.h als eine `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Ein Array von Eigenschaftennamen für die angegebene Eigenschaft-Ids. Das Array muss vorab zugeordnet, um die angeforderte Anzahl von Eigenschaftennamen enthalten und muss in der Lage, halten Sie über mindestens `cpropid``BSTR` Zeichenfolgen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebene Eigenschaftennamen müssen freigegeben werden (durch Aufrufen der `SysFreeString` Funktion) Wenn sie nicht mehr benötigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)