---
title: MemoryTypeEnum | Microsoft Docs
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
ms.openlocfilehash: 616bae99a4cb3ffafa4cdf773bce63576ed04e7a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31469593"
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
 Nur code greift auf Arbeitsspeicher.  
  
 `MemTypeData`  
 Greift auf Daten oder Stack-Speicher.  
  
 `MemTypeStack`  
 Greift auf nur Stapelspeicher.  
  
 `MemTypeAny`  
 Greift auf eine beliebige Art von Speicher.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zum Übergeben der [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) Methode, um den Zugriff auf verschiedene Arten von Arbeitsspeicher zu beschränken.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)