---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "FIELD_MODIFIERS-enumeration"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt Modifizierer für einen Feldtyp an.  
  
## Syntax  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Mitglieder  
 FIELD\_MOD\_ACCESS\_TYPE  
 Gibt an, dass das Feld nicht zugegriffen werden kann.  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 Gibt an, dass das Feld öffentlichen Zugriff hat.  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 Gibt an, dass das Feld Zugriff geschützt ist.  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 Gibt an, dass das Feld privaten Zugriff hat.  
  
 FIELD\_MOD\_NOMODIFIERS  
 Gibt an, dass das Feld keine Modifizierer verfügt.  
  
 FIELD\_MOD\_STATIC  
 Gibt an, dass das Feld statisch ist.  
  
 FIELD\_MOD\_CONSTANT  
 Gibt an, dass das Feld eine Konstante handelt.  
  
 FIELD\_MOD\_TRANSIENT  
 Gibt an, dass das Feld flüchtig ist.  
  
 FIELD\_MOD\_VOLATILE  
 Gibt an, dass das Feld flüchtig ist.  
  
 FIELD\_MOD\_ABSTRACT  
 Gibt an, dass das Feld abstrakt ist.  
  
 FIELD\_MOD\_NATIVE  
 Gibt an, dass das Feld systemeigen ist.  
  
 FIELD\_MOD\_SYNCHRONIZED  
 Gibt an, dass das Feld synchronisiert wird.  
  
 FIELD\_MOD\_VIRTUAL  
 Gibt an, dass das Feld virtuell ist.  
  
 FIELD\_MOD\_INTERFACE  
 Gibt an, dass das Feld eine Schnittstelle ist.  
  
 FIELD\_MOD\_FINAL  
 Gibt an, dass das Feld in der endgültigen Form vorliegt.  
  
 FIELD\_MOD\_SENTINEL  
 Gibt an, dass das Feld ein Sentinel ist.  
  
 FIELD\_MOD\_INNERCLASS  
 Gibt an, dass das Feld eine interne Klasse ist.  
  
 FIELD\_TYPE\_OPTIONAL  
 Gibt an, dass das Feld optional ist.  
  
 FIELD\_MOD\_BYREF  
 Gibt an, dass das Feld ein Argument verweisen.  Dies ist insbesondere für Methodenargumente.  
  
 FIELD\_MOD\_HIDDEN  
 Gibt an, dass das Feld in einem anderen Kontext ausgeblendet oder angezeigt werden muss. Beispielsweise statische lokale Variablen [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 Gibt an, dass das Feld ein Objekt mit einer `IUnknown`\-Schnittstelle darstellt.  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 Gibt an, dass das Feld über einen besonderen Namen, z. B. `.ctor` für einen Konstruktor \(nur[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] \) verfügt.  
  
 FIELD\_MOD\_HIDEBYSIG  
 Gibt an, dass das Feld über das `Overloads`\-Schlüsselwort, das darauf angewendet wird \(nur[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] \).  
  
 FIELD\_MOD\_WRITEONLY  
 Gibt an, dass das Feld lesegeschützt ist.  Dieser Wert wird nicht in `FIELD_MOD_ALL`enthalten, da der einzige Verwendung solcher lesegeschützten Feldern für die Funktionsauswertung ist.  Ein Benutzer muss sich um `FIELD_MOD_WRITEONLY` Felder explizit anfordern.  
  
 FIELD\_MOD\_ACCESS\_MASK  
 Gibt eine Maske für Feld des Zugriffs an.  
  
 FIELD\_MOD\_MASK  
 Gibt eine Maske für Feldmodifizierer an.  
  
## Hinweise  
 Wird für den `dwModifiers`\-Member der [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.  
  
 Diese Werte werden auch zur [\[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)\-Methode zum Filtern nach bestimmten Feldern übergeben.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [\[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)