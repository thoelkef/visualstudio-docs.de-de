---
title: IDiaPropertyStorage::Enum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0fe51224a4b4a5abc73a3edb7a2caf239d32efb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Ruft einen Enumerator für die Eigenschaften in dieser Gruppe ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppenum`  
 [out] Gibt ein `IEnumSTATPROPSTG` Objekt (im Namespace Microsoft.VisualStudio.OLE.Interop), das eine Enumeration von Eigenschaften darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)