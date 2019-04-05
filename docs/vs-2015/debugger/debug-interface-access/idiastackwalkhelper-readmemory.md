---
title: IDiaStackWalkHelper::readMemory | Microsoft-Dokumentation
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961677"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest einen Block von Daten aus der ausführbaren Datei Image im Arbeitsspeicher.  
  
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
 [in] Ein Wert aus der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumeration, die den Typ des Arbeitsspeichers zu lesen.  
  
 va  
 [in] Virtuelle Adresse in das Image aus dem gelesen werden soll.  
  
 `cbData`  
 [in] Die Größe des Datenpuffers in Byte.  
  
 `pcbData`  
 [out] Gibt die Anzahl der tatsächlich gelesenen Bytes. Wenn `pbData` ist `NULL`, ist dies die Gesamtanzahl der Bytes der Daten zur Verfügung.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit dem Arbeitsspeicher lesen gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)
