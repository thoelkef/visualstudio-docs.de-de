---
title: 'IDiaStackWalkHelper:: Read Memory | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150059"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest einen Datenblock aus dem Image der ausführbaren Datei im Arbeitsspeicher.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 in Ein Wert aus der [MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) -enumerationsenumeration, der den Typ des zu lesenden Speichers angibt.  
  
 va  
 in Die virtuelle Adresse im Abbild, ab der der Lesevorgang begonnen werden soll.  
  
 `cbData`  
 in Die Größe des Daten Puffers in Bytes.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der tatsächlich gelesenen Bytes zurück. Wenn `pbData` ist `NULL` , dann ist dies die Gesamtanzahl der verfügbaren Daten bytes.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit dem gelesenen Speicher gefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)
