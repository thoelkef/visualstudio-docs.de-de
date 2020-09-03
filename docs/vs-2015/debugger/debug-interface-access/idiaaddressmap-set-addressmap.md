---
title: 'IDiaAddressMap:: set_addressMap | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198649"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt eine Adress Zuordnung zur Unterstützung von Bild layoutübersetzungen bereit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 in Die Anzahl der Elemente im- `data` Parameter.  
  
 `data[]`  
 in Ein Array von [DiaAddressMapEntry-Struktur](../../debugger/debug-interface-access/diaaddressmapentry.md) Strukturen, die die Übersetzungs Zuordnung definieren.  
  
 `imagetoSymbols`  
 [in] `TRUE` , wenn der- `data` Parameter eine Zuordnung vom neuen Bild Layout zum ursprünglichen Layout definiert (wie von den Debugsymbolen beschrieben). `FALSE` Wenn `data` eine Zuordnung zum neuen Bild Layout ist, das aus dem ursprünglichen Layout entnommen wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 In der Regel ruft der Dia Adress Übersetzungs Zuordnungen aus der Programm Datenbankdatei (. pdb) ab. Wenn diese Werte fehlen, wird die [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) -Methode zweimal aufgerufen, wobei der `imagetoSymbols` -Parameter auf `TRUE` und einmal mit dem- `imagetoSymbols` Parameter auf festgelegt ist `FALSE` . Adress Zuordnungs Übersetzungen können nicht mithilfe der Methode [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) aktiviert werden, es sei denn, beide Übersetzungs Zuordnungen werden bereitgestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DiaAddressMapEntry-Struktur](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
