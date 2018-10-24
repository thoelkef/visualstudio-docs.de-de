---
title: IDiaStackWalkHelper::readMemory | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76b054d004e6c62f9d36ca5fcebe1a7f0476fbfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825854"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Liest einen Block von Daten aus der ausführbaren Datei Image im Arbeitsspeicher.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
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
  
 VA  
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