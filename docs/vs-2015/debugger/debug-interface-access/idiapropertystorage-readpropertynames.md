---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957275"
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
