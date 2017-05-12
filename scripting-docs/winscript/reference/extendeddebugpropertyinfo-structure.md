---
title: "ExtendedDebugPropertyInfo-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo-Struktur"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo-Struktur
Erweitert die `DebugPropertyInfo`\-Struktur mit zusätzlichen Member, um die erweiterte Eigenschaft zu kennzeichnen.  
  
## Syntax  
  
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
  
## Mitglieder  
 `dwValidFields`  
 Ein aufgelisteter Datentyp verwendet, um anzugeben, den Felder initialisiert werden.  
  
 `bstrName`  
 Der Eigenschaftenname in einem Kontext.  
  
 `bstrType`  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 `bstrValue`  
 Der Eigenschaftswert als formatierte Zeichenfolge.  
  
 `bstrFullName`  
 Der vollständige Name der Eigenschaft.  
  
 `dwAttrib`  
 Eine Enumeration, die die Flags für die Debugsitzung Eigenschaft angibt, schreibt in.  
  
 `pDebugProp`  
 `IDebugProperty`\-Objekt entsprechend diesem `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Die Dispatchidentifikation  
  
 `nType`  
 Der erweiterte Eigenschaftentyp.  
  
 `varValue`  
 Der erweiterte Eigenschaftswert, wenn er in VARIANTE passen.  
  
 `plbValue`  
 Die tatsächlichen Datenbytes des Eigenschaftswerts.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`\-Objekt entsprechend diesem `ExtendedDebugPropertyInfo`.  
  
## Siehe auch  
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty\-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)