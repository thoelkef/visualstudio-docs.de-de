---
title: DiaAddressMapEntry | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164356"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beschreibt einen Eintrag in einer Adress Zuordnung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elemente  
 `rva`  
 Eine relative virtuelle Adresse (RVA) in Image A.  
  
 `rvaTo`  
 Die relative virtuelle Adresse `rva` wird in Image B zugeordnet.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Adress Zuordnung bietet eine Übersetzung von einem Bild Layout (a) zu einem anderen (B). Ein Array von `DiaAddressMapEntry` durch sortierten Strukturen `rva` definiert eine Adress Zuordnung.  
  
 Führen Sie die folgenden Schritte aus, um eine Adresse `addrA` in Image a in eine Adresse zu übersetzen `addrB` :  
  
1. Durchsuchen Sie die Zuordnung für den Eintrag `e` mit dem größten `rva` kleiner als oder gleich `addrA` .  
  
2. Legen Sie `delta = addrA – e.rva` fest.  
  
3. Legen Sie `addrB = e.rvaTo + delta` fest.  
  
   Ein Array von- `DiaAddressMapEntry` Strukturen wird an die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode übermittelt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: dia2.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
