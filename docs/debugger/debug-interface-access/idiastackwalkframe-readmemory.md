---
title: 'Idiastackwalkframe:: ReadMemory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d23b46f0f487bddc678814e41b5cb96331ff46c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Liest Arbeitsspeicher aus Image an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 [in] Eines der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumerationswerte, der die Art des Arbeitsspeichers, den Zugriff auf angibt.  
  
 `va`  
 [in] Virtuelle Adressspeicherort in Abbildung Lesevorgang begonnen werden soll.  
  
 `cbData`  
 [in] Die Größe des Datenpuffers in Bytes.  
  
 `pcbData`  
 [out] Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes der Daten verfügbar.  
  
 `data`  
 [out] Ein Puffer, die mit Daten aus der angegebenen Position ausgefüllt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)