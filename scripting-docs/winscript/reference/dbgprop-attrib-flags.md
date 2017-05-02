---
title: "DBGPROP_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_ATTRIB_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DBGPROP_ATTRIB_FLAGS
Beschreibt verschiedene Attribute für ein `IDebugProperty`.  Member der `DebugPropertyInfo`\-Struktur.  
  
## Syntax  
  
```  
enum { DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,    DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,    DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,    DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,    DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,    DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,    DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,    DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,    DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,    DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,    DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,    DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,    DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,    DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,    DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,    DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000    DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000, };   
```  
  
## Mitglieder  
 DBGPROP\_ATTRIB\_NO\_ATTRIB  
 Gibt keine Attribute an.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_INVALID  
 Gibt an, dass der Wert im `DebugPropertyInfo::bstrValue` ungültig ist.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_EXPANDABLE  
 Gibt an, dass der Verweis oder die Eigenschaft über untergeordnete Elemente verfügt.  
  
 DBGPROP\_ATTRIB\_VALUE\_READONLY  
 Gibt an, dass der Wert schreibgeschützt ist.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PUBLIC  
 Gibt ein Objekt mit öffentlichem Zugriff an.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PRIVATE  
 Gibt ein Objekt mit privatem Zugriff an.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PROTECTED  
 Gibt ein Objekt mit geschütztem Zugriff an.  
  
 DBGPROP\_ATTRIB\_ACCESS\_FINAL  
 Gibt ein Objekt mit endgültigem Zugriff an.  
  
 DBGPROP\_ATTRIB\_STORAGE\_GLOBAL  
 Zeigt einen globalen Speicher an.  
  
 DBGPROP\_ATTRIB\_STORAGE\_STATIC  
 Zeigt einen statischen Speicher an.  
  
 DBGPROP\_ATTRIB\_STORAGE\_FIELD  
 Kennzeichnet ein Objekt, das eine Eigenschaft ist.  
  
 DBGPROP\_ATTRIB\_STORAGE\_VIRTUAL  
 Gibt einen virtuellen Speicher an.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_CONSTANT  
 Gibt an, dass der Objekttyp konstant ist.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_SYNCHRONIZED  
 Gibt an, dass dieser Steckplatz Thread\-synchronisiert ist.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_VOLATILE  
 Gibt an, dass dieser Steckplatz in Bezug auf dauerhafte Speicherung flüchtig ist.  
  
 DBGPROP\_ATTRIB\_HAS\_EXTENDED\_ATTRIBS  
 Gibt an, dass dieser Steckplatz über Attribute über und jenseits dieser vordefinierten Bits verfügt.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_RETURN\_VALUE  
 Gibt an, dass der Wert ein Rückgabewert einer Funktion ist.  
  
## Hinweise  
 Diese Markierungen werden auch verwendet, um untergeordnete Elemente eines Objekts zu filtern.  Die Werte können mit einem bitweisen OR\-Operator kombiniert werden.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)