---
title: Extendeddebugpropertyinfo-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575834"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo-Struktur
Erweitert die `DebugPropertyInfo` Struktur mit zusätzlichen Membern, um die erweiterte Eigenschaft zu charakterisieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Member  
 `dwValidFields`  
 Ein enumerierter Datentyp, der verwendet wird, um anzugeben, welche Felder initialisiert werden.  
  
 `bstrName`  
 Der Eigenschaftsname innerhalb eines Kontexts.  
  
 `bstrType`  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 `bstrValue`  
 Der Eigenschafts Wert als formatierte Zeichenfolge.  
  
 `bstrFullName`  
 Der vollständige Name der Eigenschaft.  
  
 `dwAttrib`  
 Eine Enumeration, die die Flags für die Debug-Eigenschafts Attribute angibt.  
  
 `pDebugProp`  
 `IDebugProperty` Objekt, das diesem `ExtendedDebugPropertyInfo` entspricht.  
  
 `nDISPID`  
 Die Dispatch-ID.  
  
 `nType`  
 Der erweiterte Eigenschaftentyp.  
  
 `varValue`  
 Der erweiterte Eigenschafts Wert, wenn der Wert in Variant eingefügt werden kann.  
  
 `plbValue`  
 Die tatsächlichen Daten Bytes des Eigenschafts Werts.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` Objekt, das diesem `ExtendedDebugPropertyInfo` entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugpropertyinfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)    
 [Idebugproperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)    
 [Idebugextendecodproperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)    
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)