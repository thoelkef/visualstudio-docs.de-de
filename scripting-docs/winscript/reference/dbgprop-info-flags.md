---
title: "DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS"
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DBGPROP_INFO_FLAGS
Wird verwendet, um `DebugPropertyInfo` Felder angeben  
  
## Syntax  
  
```  
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
  
## Mitglieder  
 DBGPROP\_INFORMATION\_NAME  
 Initialisiert das `bstrName` Feld.  
  
 DBGPROP\_INFORMATION\_TYPE  
 Initialisiert das `bstrType` Feld.  
  
 DBGPROP\_INFORMATION\_VALUE  
 Initialisiert das `bstrValue` Feld.  
  
 DBGPROP\_INFORMATION\_FULLNAME  
 Initialisiert das `bstrFullName` Feld.  
  
 DBGPROP\_INFORMATION\_ATTRIBUTES  
 Initialisiert das `dwAttrib` Feld.  
  
 DBGPROP\_INFORMATION\_DEBUGPROP  
 Initialisiert das `pDebugProp` Feld, das eine `IDebugProperty`\-Schnittstelle enthält.  
  
 DBGPROP\_INFORMATION\_AUTOEXPAND  
 Gibt an, dass das Wertsfeld den AUTO\-erweiterten Wert enthalten soll, wenn verfügbar, für diesen Objekttyp.  
  
## Siehe auch  
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)