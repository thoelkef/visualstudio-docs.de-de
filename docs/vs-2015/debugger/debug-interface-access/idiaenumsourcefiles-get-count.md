---
title: 'IDiaEnumSourceFiles:: get_Count | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get_Count method
ms.assetid: 04083b97-e1ac-4baf-bf5a-50a4dc1c6f27
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb79b6ce3706f83a37169e0d3c6cb28165b426fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189792"
---
# <a name="idiaenumsourcefilesget_count"></a>IDiaEnumSourceFiles::get_Count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Anzahl der Quelldateien ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 vorgenommen Gibt die Anzahl der Quelldateien zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)
