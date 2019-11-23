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
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572581"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Wird verwendet, um `DebugPropertyInfo` Felder anzugeben.  
  
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
 Initialisiert das `bstrName` Feld.  
  
 DBGPROP_INFO_TYPE  
 Initialisiert das `bstrType` Feld.  
  
 DBGPROP_INFO_VALUE  
 Initialisiert das `bstrValue` Feld.  
  
 DBGPROP_INFO_FULLNAME  
 Initialisiert das `bstrFullName` Feld.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Initialisiert das `dwAttrib` Feld.  
  
 DBGPROP_INFO_DEBUGPROP  
 Initialisiert das `pDebugProp` Feld, das eine `IDebugProperty` Schnittstelle enthält.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Gibt an, dass das Wertfeld für diesen Objekttyp den automatisch erweiterten Wert enthalten soll, falls verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugpropertyinfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)