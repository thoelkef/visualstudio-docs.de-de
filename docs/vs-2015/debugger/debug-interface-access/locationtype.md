---
title: LocationType | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154203"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Art der Speicherort Informationen an, die in einem Symbol enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elemente  
 `LocIsNull`  
 Die Standortinformationen sind nicht verfügbar.  
  
 `LocIsStatic`  
 Der Speicherort ist statisch.  
  
 `LocIsTLS`  
 Der Speicherort befindet sich im lokalen Thread Speicher.  
  
 `LocIsRegRel`  
 Location ist Register-relative.  
  
 `LocIsThisRel`  
 Location ist `this` -relative.  
  
 `LocIsEnregistered`  
 Standort befindet sich in einem Register.  
  
 `LocIsBitField`  
 Der Speicherort befindet sich in einem Bitfeld.  
  
 `LocIsSlot`  
 Location ist ein MSIL-Slot (Microsoft Intermediate Language).  
  
 `LocIsIlRel`  
 Location ist MSIL-relative.  
  
 `LocInMetaData`  
 Der Speicherort ist in den Metadaten.  
  
 `LocIsConstant`  
 Der Speicherort ist ein konstanter Wert.  
  
 `LocTypeMax`  
 Die Anzahl der Speicherort Typen in dieser Enumeration.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften, die für die [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Schnittstelle verfügbar sind, hängen von der Position des Symbols in der Bilddatei ab. Weitere Informationen finden Sie unter [Symbol Speicherorte](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymmetribol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)
