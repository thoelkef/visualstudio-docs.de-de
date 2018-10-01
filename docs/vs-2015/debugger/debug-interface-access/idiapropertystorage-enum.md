---
title: IDiaPropertyStorage::Enum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e7710881233d37089ddb9c623194d6b19cdfb2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523674"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaPropertyStorage::Enum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-enum).  
  
Ruft einen Enumerator für Eigenschaften in dieser Gruppe ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppenum`  
 [out] Gibt eine `IEnumSTATPROPSTG` -Objekt (im Namespace Microsoft.VisualStudio.OLE.Interop), die eine Enumeration von Eigenschaften darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



