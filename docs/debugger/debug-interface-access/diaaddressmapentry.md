---
title: DiaAddressMapEntry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1324ea79ec60a61e315253573b9d4aa3ced2695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Beschreibt einen Eintrag in einer-Adresszuordnung.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elements  
 `rva`  
 Eine relative virtuelle Adresse (RVA) in Abbildung a  
  
 `rvaTo`  
 Die relative virtuelle Adresse `rva` in Abbildung b zugeordnet ist  
  
## <a name="remarks"></a>Hinweise  
 Eine-Adresszuordnung enthält eine Übersetzung aus einem Bildlayout (A) in einem anderen (B). Ein Array von `DiaAddressMapEntry` Strukturen sortiert nach `rva` eine-Adresszuordnung definiert.  
  
 Um eine Adresse zu übersetzen `addrA`, im Bild ein, das eine Adresse `addrB`, führen Sie in Abbildung B die folgenden Schritte aus:  
  
1.  Suchen Sie die Zuordnung für den Eintrag `e`, mit dem größten `rva` kleiner als oder gleich `addrA`.  
  
2.  Set `delta = addrA - e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 Ein Array von `DiaAddressMapEntry` Strukturen wird zum Übergeben der [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: dia2.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)