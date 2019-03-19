---
title: DebugPropertyInfo-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 99208626b41f2463178bccecf73c21a1d15fa765
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155744"
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