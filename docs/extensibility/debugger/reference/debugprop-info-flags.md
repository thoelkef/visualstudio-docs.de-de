---
title: "DEBUGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS-enumeration"
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche über eine Debug\- Eigenschaftenobjekt Informationen abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## Mitglieder  
 DEBUGPROP\_INFORMATION\_FULLNAME  
 Initialisieren Sie das Feld `bstrFullName` \/verwenden.  
  
 DEBUGPROP\_INFORMATION\_NAME  
 Initialisieren Sie das Feld `bstrName` \/verwenden.  
  
 DEBUGPROP\_INFORMATION\_TYPE  
 Initialisieren Sie das Feld `bstrType` \/verwenden.  
  
 DEBUGPROP\_INFORMATION\_VALUE  
 Initialisieren Sie das Feld `bstrValue` \/verwenden.  
  
 DEBUGPROP\_INFORMATION\_ATTRIB  
 Initialisieren Sie das Feld `dwAttrib` \/verwenden.  
  
 DEBUGPROP\_INFORMATION\_PROP.  
 Initialisieren Sie verwenden das\/`pProperty` Feld, das eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle enthält.  
  
 DEBUGPROP\_INFORMATION\_VALUE\_AUTOEXPAND  
 Gibt an, dass das Feld Wert den AUTO\-erweiterten Wert enthalten soll, falls verfügbar, für diesen Objekttyp.  
  
 DEBUGPROP\_INFORMATION\_VALUE\_NOFUNCEVAL  
 Veraltet.  
  
 DEBUGPROP\_INFORMATION\_VALUE\_RAW  
 Geben Sie keine verschönerten Werte oder Member zurück \(das heißt formatieren Sie nicht die Werte\).  
  
 DEBUGPROP\_INFORMATION\_VALUE\_NO\_TOSTRING  
 Geben Sie keine besonderen synthetischen Werte zurück \(z. B. rufen Sie nicht `ToString()` für ein Objekt auf, um einen Wert zu erstellen\).  
  
 DEBUGPROP\_INFORMATION\_NONE  
 Gibt an, dass keine Flags festgelegt werden.  
  
 DEBUGPROP\_INFORMATION\_STANDARD  
 Initialisieren Sie `dwAttrib`, `bstrName`\/verwenden, `bstrType`, und `bstrValue` Felder.  
  
 DEBUGPROP\_INFORMATION\_All  
 Gibt eine Maske aller Flags an.  
  
## Hinweise  
 Diese Werte werden an den [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)und [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)\-Methode übergeben, um anzugeben, welche Felder der [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch für den `dwFields`\-Member der `DEBUG_PROPERTY_INFO` Struktur verwendet, um anzugeben, welche Felder der Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [\[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)