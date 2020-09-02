---
title: IDiaStackWalkFrame::readMemory | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150160"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest Speicher aus dem Image.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Einer der [MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) -Enumerationswerte, der die Art des Arbeitsspeichers angibt, auf den zugegriffen werden soll.  
  
 `va`  
 in Der Speicherort der virtuellen Adresse in Image zum beginnen des Lesens.  
  
 `cbData`  
 in Größe des Daten Puffers in Bytes.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` ist `NULL` , `pcbData` enthält die Gesamtanzahl der verfügbaren Daten bytes.  
  
 `data`  
 vorgenommen Ein Puffer, der mit Daten aus der angegebenen Position ausgefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
