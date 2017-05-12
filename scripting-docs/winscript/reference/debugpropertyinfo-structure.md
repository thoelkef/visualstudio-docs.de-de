---
title: "DebugPropertyInfo-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo-Struktur"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo-Struktur
Beschreibt ein Objekt einer hierarchischen Natur, Namen, Typ und Wert verfügt.  Sie wird verwendet, um die DebugEigenschaften von lokalen Variablen, Parameter, Überwachungsvariablen und und Register zu beschreiben.  
  
## Syntax  
  
```  
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
  
## Mitglieder  
 dwValidFields  
 Ein aufgelisteter Datentyp verwendet, um anzugeben, den Felder initialisiert werden.  
  
 bstrName  
 Der Eigenschaftenname in einem Kontext.  
  
 bstrType  
 Der Eigenschaftentyp, als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert, als formatierte Zeichenfolge.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 dwAttrib  
 Eine Enumeration, die die Flags für die Debugsitzung Eigenschaft angibt, schreibt in.  
  
 pDebugProp  
 `IDebugProperty` beschrieben durch die Informationen in dieser `DebugPropertyInfo`\-Struktur.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)