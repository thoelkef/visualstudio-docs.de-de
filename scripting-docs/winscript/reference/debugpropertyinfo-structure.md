---
title: DebugPropertyInfo-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47c0f6a359341d19b99c1ce8c099ebf1c6d6a1ff
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088984"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo-Struktur
Beschreibt ein Objekt von einer hierarchischen Aufbaus, der Name, Typ und Wert verfügt. Es wird verwendet, um die Debugeigenschaften der lokalen Variablen, Parameter, überwachen Sie Variablen und Ausdrücke beschrieben und registriert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Member  
 dwValidFields  
 Ein Aufzählungsdatentyp verwendet, um anzugeben, welche Felder initialisiert werden.  
  
 bstrName  
 Der Eigenschaftenname in einem Kontext.  
  
 bstrType  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert als formatierte Zeichenfolge.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 dwAttrib  
 Eine Enumeration, die angibt, die Flags für die Attribute der Debug-Eigenschaft.  
  
 pDebugProp  
 Die `IDebugProperty` beschrieben werden, indem Sie die Informationen in diesem `DebugPropertyInfo` Struktur.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)