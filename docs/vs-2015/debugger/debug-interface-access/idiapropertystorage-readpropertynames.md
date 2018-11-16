---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft-Dokumentation
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
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8523dfb795f63abdecd9be1f08ec68371355fbde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759556"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft entsprechende Zeichenfolgennamen für angegebenen Eigenschaftenbezeichner.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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



