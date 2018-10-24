---
title: LocationType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d1c9ff2dce8918d5bcc75c8504e5af133ea5e43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836154"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Art der Standortinformationen in ein Symbol an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Speicherort ist statisch.  
  
 `LocIsTLS`  
 Speicherort ist im lokalen Threadspeicher.  
  
 `LocIsRegRel`  
 Speicherort ist relativ registrieren.  
  
 `LocIsThisRel`  
 Speicherort ist `this`-relative.  
  
 `LocIsEnregistered`  
 Speicherort ist in einem Register.  
  
 `LocIsBitField`  
 Speicherort ist in einem Bitfeld.  
  
 `LocIsSlot`  
 Speicherort ist ein Microsoft Intermediate Language (MSIL)-Slot.  
  
 `LocIsIlRel`  
 Der Speicherort ist relativ MSIL.  
  
 `LocInMetaData`  
 Speicherort ist in den Metadaten.  
  
 `LocIsConstant`  
 Speicherort ist in einem konstanten Wert.  
  
 `LocTypeMax`  
 Die Anzahl der Typen in dieser Enumeration.  
  
## <a name="remarks"></a>Hinweise  
 Die Eigenschaften für die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Schnittstelle hängen Speicherort des Symbols, in der Imagedatei. Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)



