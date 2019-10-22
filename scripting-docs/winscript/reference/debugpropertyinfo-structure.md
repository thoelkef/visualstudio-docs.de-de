---
title: Debugpropertyinfo-Struktur | Microsoft-Dokumentation
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
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575068"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo-Struktur
Beschreibt ein Objekt der hierarchischen Natur, das den Namen, den Typ und den Wert hat. Es wird verwendet, um die Debugeigenschaften lokaler Variablen, Parameter, Überwachungs Variablen und-Ausdrücke sowie Register zu beschreiben.  
  
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
 dwvalidfields  
 Ein enumerierter Datentyp, der verwendet wird, um anzugeben, welche Felder initialisiert werden.  
  
 bstrName  
 Der Eigenschaftsname innerhalb eines Kontexts.  
  
 bstrintype  
 Der Eigenschaftentyp, als formatierte Zeichenfolge.  
  
 bstrauvalue  
 Der Eigenschafts Wert als formatierte Zeichenfolge.  
  
 bstraufullname  
 Der vollständige Name der Eigenschaft.  
  
 dwattenb  
 Eine Enumeration, die die Flags für die Debug-Eigenschafts Attribute angibt.  
  
 pdebug-Prop  
 Die `IDebugProperty`, die durch die Informationen in dieser `DebugPropertyInfo` Struktur beschrieben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugproperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)