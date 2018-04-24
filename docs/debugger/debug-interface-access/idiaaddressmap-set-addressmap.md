---
title: 'Idiaaddressmap:: Set_addressmap | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1c934dc998818973b5de4106c3df952ad24f22f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Stellt eine Adresse-Karte, um das Image Layout Übersetzungen unterstützen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 [in] Die Anzahl der Elemente in der `data` Parameter.  
  
 `data[]`  
 [in] Ein Array von [DiaAddressMapEntry Struktur](../../debugger/debug-interface-access/diaaddressmapentry.md) Strukturen, die die Zuordnung der Übersetzung zu definieren.  
  
 `imagetoSymbols`  
 [in] `TRUE` Wenn die `data` Parameter definiert eine Zuordnung aus dem neuen Image Layout des ursprünglichen Layouts (wie durch den Debugsymbolen beschrieben). `FALSE` Wenn `data` ist eine Zuordnung für das neue Image Layout des ursprünglichen Layouts entnommen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Normalerweise ruft der DIA Adresse Übersetzung Maps über die Programmdatenbankdatei (.pdb) ab. Wenn diese Werte fehlen, werden die [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Methode zweimal aufgerufen wird einmal mit der `imagetoSymbols` Parameter festgelegt wird, um `TRUE` und einmal mit der `imagetoSymbols` Parameter festgelegt wird, um `FALSE`. Adressübersetzung der Zuordnung können nicht aktiviert werden, mithilfe der [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) Methode, wenn beide Übersetzung Maps bereitgestellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [DiaAddressMapEntry-Struktur](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)