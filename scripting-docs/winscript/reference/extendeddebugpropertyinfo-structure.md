---
title: ExtendedDebugPropertyInfo-Struktur | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo-Struktur
Erweitert die `DebugPropertyInfo` Struktur mit zusätzlichen Mitgliedern hinzu, die erweiterte Eigenschaft charakterisieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Enumerierten Datentyps verwendet, um anzugeben, welche Felder initialisiert werden.  
  
 `bstrName`  
 Der Eigenschaftsname in einem Kontext.  
  
 `bstrType`  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 `bstrValue`  
 Der Eigenschaftswert als eine formatierte Zeichenfolge.  
  
 `bstrFullName`  
 Der vollständige Name der Eigenschaft.  
  
 `dwAttrib`  
 Eine Enumeration, die die Flags für die Debug-Eigenschaftenattribute angibt.  
  
 `pDebugProp`  
 `IDebugProperty`Objekt, das diesem `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Die Dispatch-Id.  
  
 `nType`  
 Der Typ des erweiterten Eigenschaft.  
  
 `varValue`  
 Der Erweiterte Eigenschaftenwert, wenn es in der Variante passen.  
  
 `plbValue`  
 Die tatsächlichen Datenbytes des Eigenschaftswerts.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`Objekt, das diesem `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Siehe auch  
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)