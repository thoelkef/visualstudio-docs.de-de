---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d51eaed785932703a5eb97714be8dc7b407fc81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891816"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Ruft entsprechende Zeichenfolgennamen für angegebenen Eigenschaftenbezeichner.  
  
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
 [in] Array von Eigenschaften-Ids für die Namen die abzurufenden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Ein Array von Eigenschaftennamen für die angegebene Eigenschaft-Ids. Das Array müssen nicht vorab zugewiesen ist, um die angeforderte Anzahl der Namen von aufzunehmen und muss in der Lage, enthalten mindestens `cpropid``BSTR` Zeichenfolgen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die zurückgegebenen Eigenschaftennamen müssen freigegeben werden (durch Aufrufen der `SysFreeString` Funktion) Wenn sie nicht mehr benötigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)