---
title: MemoryTypeEnum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a8dcf657933cf62f3f2173bb89dadd1366b0cec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822942"
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