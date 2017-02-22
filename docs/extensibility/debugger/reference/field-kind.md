---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "FIELD_KIND-enumeration"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Art des Felds in einem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt an.  
  
## Syntax  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Mitglieder  
 FIELD\_KIND\_TYPE  
 Gibt an, dass auf das Feld nur über einen Typ ist.  
  
 FIELD\_KIND\_SYMBOL  
 Gibt an, dass das Feld ein Symbol, mit dem Typ, Name und andere Informationen an.  
  
 FIELD\_TYPE\_PRIMITIVE  
 Gibt an, dass das Feld ein Grunddatentyp ist.  
  
 FIELD\_TYPE\_STRUCT  
 Gibt an, dass das Feld Struktur handelt.  
  
 FIELD\_TYPE\_CLASS  
 Gibt an, dass das Feld eine Klasse ist.  
  
 FIELD\_TYPE\_INTERFACE  
 Gibt an, dass das Feld eine Schnittstelle ist.  
  
 FIELD\_TYPE\_UNION  
 Gibt an, dass das Feld Union ist.  
  
 FIELD\_TYPE\_ARRAY  
 Gibt an, dass das Feld ein Array ist.  
  
 FIELD\_TYPE\_METHOD  
 Gibt an, dass das Feld eine Methode handelt.  
  
 FIELD\_TYPE\_BLOCK  
 Gibt an, dass das Feld ein Block befindet.  
  
 FIELD\_TYPE\_POINTER  
 Gibt an, dass das Feld ein Zeiger ist.  
  
 FIELD\_TYPE\_ENUM  
 Gibt an, dass das Feld ein aufgelisteter Datentyp ist.  
  
 FIELD\_TYPE\_LABEL  
 Gibt an, dass das Feld eine Bezeichnung darstellt.  
  
 FIELD\_TYPE\_TYPEDEF  
 Gibt an, dass das Feld eine Typdefinition ist.  
  
 FIELD\_TYPE\_BITFIELD  
 Gibt an, dass das Feld ein Bitfeld ist.  
  
 FIELD\_TYPE\_NAMESPACE  
 Gibt an, dass das Feld ein Namespace befindet.  
  
 FIELD\_TYPE\_MODULE  
 Gibt an, dass das Feld ein Modul ist.  
  
 FIELD\_TYPE\_DYNAMIC  
 Gibt an, dass das Feld dynamisch ist.  
  
 FIELD\_TYPE\_PROP  
 Gibt an, dass das Feld eine Eigenschaft ist.  
  
 FIELD\_TYPE\_INNERCLASS  
 Gibt an, dass das Feld eine interne Klasse ist.  
  
 FIELD\_TYPE\_REFERENCE  
 Gibt an, dass das Feld ein Verweis ist.  
  
 FIELD\_TYPE\_EXTENDED  
 Für zukünftige Verwendung reserviert.  
  
 FIELD\_SYM\_MEMBER  
 Gibt an, dass das Feld ein Member ist.  
  
 FIELD\_SYM\_LOCAL  
 Gibt an, dass das Feld lokal ist.  
  
 FIELD\_SYM\_PARAMETER  
 Gibt an, dass das Feld ein Parameter ist.  
  
 FIELD\_SYM\_THIS  
 Gibt an, dass das Feld „this“ \- Zeiger aufweist.  
  
 FIELD\_SYM\_GLOBAL  
 Gibt an, dass das Feld global ist.  
  
 FIELD\_SYM\_PROP\_GETTER  
 Gibt an, dass das Feld Eigenschaften abgerufen werden sollen.  
  
 FIELD\_SYM\_PROP\_SETTER  
 Gibt an, dass auf das Feld Eigenschaft festgelegt werden.  
  
 FIELD\_SYM\_EXTENDED  
 Für zukünftige Verwendung reserviert.  
  
 FIELD\_KIND\_MASK  
 Gibt eine Maske für Feldarten an.  
  
 FIELD\_TYPE\_MASK  
 Gibt eine Maske für Feldtypen an.  
  
 FIELD\_SYM\_MASK  
 Gibt eine Maske Symbol Informationen an.  
  
## Hinweise  
 Wird zurückgegeben [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) von einem Aufruf der Methode.  
  
 Abhängig von der Art des Felds, [QueryInterface](/visual-cpp/atl/queryinterface) der aufgerufen werden kann [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle für ein spezifischerer Form der Schnittstelle.  Wenn z. B. [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_METHOD`zurückgibt, können Sie `QueryInterface` I`DebugField` dann auf aufrufen, um die [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)\-Schnittstelle.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)