---
title: MemoryTypeEnum | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158127"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Typ des zu zuzurufenden Speichers an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 `MemTypeCode`  
 Greift nur auf den Code Speicher zu.  
  
 `MemTypeData`  
 Greift auf Daten oder den Stapel Speicher zu.  
  
 `MemTypeStack`  
 Greift nur auf den Stapel Speicher zu.  
  
 `MemTypeAny`  
 Greift auf eine beliebige Art von Arbeitsspeicher zu.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden an die [IDiaStackWalkHelper:: Read Memory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) -Methode übermittelt, um den Zugriff auf verschiedene Arbeitsspeicher Typen einzuschränken.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
