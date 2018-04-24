---
title: LocationType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb46eb1c7477f93ed63dfc4424d881886c8d0c8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
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