---
title: MemoryTypeEnum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42cfe138aa6be00628d319f01e7cccfbb4cc4f8a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040163"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Gibt den Typ des Speichers auf.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 `MemTypeCode`  
 Nur code greift auf Speicher.  
  
 `MemTypeData`  
 Greift auf Daten oder Stack-Speicher.  
  
 `MemTypeStack`  
 Greift auf nur Stapelspeicher.  
  
 `MemTypeAny`  
 Greift auf jede Art von Speicher zu.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zum Übergeben der [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) Methode, um den Zugriff auf verschiedene Arten von Speicher zu beschränken.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)