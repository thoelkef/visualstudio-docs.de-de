---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f528d377dc75f940a10f1a38ae04cc3eb71cdd22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Liest einen Block von Daten aus der ausführbaren Image im Arbeitsspeicher.  
  
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
 [in] Ein Wert aus der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumeration, die Angabe des Typs der Arbeitsspeicher zu lesen.  
  
 "VA" ist  
 [in] Virtuelle Adresse in das Abbild aus der Lesevorgang beginnen soll.  
  
 `cbData`  
 [in] Die Größe des Datenpuffers in Bytes.  
  
 `pcbData`  
 [out] Gibt die Anzahl der tatsächlich gelesenen Bytes zurück. Wenn `pbData` ist `NULL`, ist dies die Gesamtanzahl der Bytes der Daten verfügbar.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit dem Arbeitsspeicher lesen ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)