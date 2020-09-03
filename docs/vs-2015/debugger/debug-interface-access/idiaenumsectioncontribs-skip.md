---
title: 'Idiaenumsectioncontrisb:: Skip | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55dd45244779ca341a4228adf3256d42616e66d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189949"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl von Abschnitts Beiträgen in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der Abschnitts Beiträge in der zu über springenden enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` Wenn keine weiteren Abschnitts Beiträge zum Überspringen vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
