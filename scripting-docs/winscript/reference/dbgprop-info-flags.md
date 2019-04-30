---
title: DBGPROP_INFO_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c63cf941bca1965fc4a2e3997f0c0b50ebc44035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955301"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Geben Sie zum `DebugPropertyInfo` Felder  
  
## <a name="syntax"></a>Syntax  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Member  
 DBGPROP_INFO_NAME  
 Initialisiert die `bstrName` Feld.  
  
 DBGPROP_INFO_TYPE  
 Initialisiert die `bstrType` Feld.  
  
 DBGPROP_INFO_VALUE  
 Initialisiert die `bstrValue` Feld.  
  
 DBGPROP_INFO_FULLNAME  
 Initialisiert die `bstrFullName` Feld.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Initialisiert die `dwAttrib` Feld.  
  
 DBGPROP_INFO_DEBUGPROP  
 Initialisiert die `pDebugProp` Feld mit einem `IDebugProperty` Schnittstelle.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Gibt an, dass das Feld "Wert" den Wert automatisch erweitert, für diesen Objekttyp enthalten soll.  
  
## <a name="see-also"></a>Siehe auch  
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)