---
title: LocationType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3f59f33ef51eee099a8dfe5bbc5c822f217f8cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="locationtype"></a>LocationType
Gibt die Art der Standortinformationen in ein Symbol an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
enum LocationType {   
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
  
## <a name="elements"></a>Elements  
 `LocIsNull`  
 Informationen zum Speicherort ist nicht verfügbar.  
  
 `LocIsStatic`  
 Ort ist statisch.  
  
 `LocIsTLS`  
 Speicherort ist im lokalen Threadspeicher.  
  
 `LocIsRegRel`  
 Der Speicherort ist relativ zum Registrieren.  
  
 `LocIsThisRel`  
 Ist der Speicherort `this`-relative.  
  
 `LocIsEnregistered`  
 Speicherort ist in einem Register.  
  
 `LocIsBitField`  
 Speicherort ist ein Bitfeld.  
  
 `LocIsSlot`  
 Speicherort ist eine Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Der Speicherort ist relativ MSIL.  
  
 `LocInMetaData`  
 Speicherort ist in den Metadaten.  
  
 `LocIsConstant`  
 Speicherort ist ein konstanter Wert.  
  
 `LocTypeMax`  
 Die Anzahl der Typen in dieser Enumeration.  
  
## <a name="remarks"></a>Hinweise  
 Die Eigenschaften verfügbar, die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Schnittstelle hängen von der Symbolspeicherort in der Abbilddatei. Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)