---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS-Enumerationen"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt verschiedene Attribute für [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oder eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Schnittstelle.  Mitglieder der [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur.  
  
## Syntax  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```c#  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## Mitglieder  
 DBG\_ATTRIB\_NONE  
 Gibt keine Attribute auf.  
  
 DBG\_ATTRIB\_ALL  
 Gibt alle Attribute an.  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 Gibt an, dass der Verweis oder die Eigenschaft über untergeordnete Elemente verfügt.  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 Gibt an, dass eine ID für dieses Objekt erstellt wurde.  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 Gibt an, dass eine ID für dieses Objekt erstellt werden kann.  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 Gibt an, dass der Wert schreibgeschützt ist.  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 Gibt an, dass der Wert ein Fehler ist.  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 Gibt an, dass die Auswertung einen Nebeneffekt hat.  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 Gibt an, dass diese Eigenschaft tatsächlich ein Container Überladungen ist.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` boolesch ist.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` boolesch und `TRUE`ist.  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` ungültig ist.  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` „*Keine Ursache*“ \(Netzwerkadressenübersetzung\).  Netzwerkadressenübersetzung beschreibt ein Register flag in Intel\-64\-Bit\-Prozessoren, das verzögerte spekulative Ausnahmen angibt.  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` möglicherweise AUTO\-erweitert wurde.  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 Gibt an, dass eine Evaluierung zeitgesteuertes\-heraus verfügt.  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 Gibt an, dass der Wert in `DEBUG_PROPERTY_INFO::bstrValue` durch eine unformatierte Zeichenfolge dargestellt werden kann.  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 Gibt an, dass diese Eigenschaft über mindestens einen benutzerdefinierten Viewer zugeordnet ist.  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 Gibt ein Objekt an, das weder `public`, `private`Typ `protected` weiterhin Zugriff hat.  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 Gibt ein Objekt an, das den öffentlichen Zugriff hat.  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 Gibt ein Objekt an, das privaten Zugriff hat.  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 Gibt ein Objekt an, das Zugriff geschützt ist.  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 Gibt ein Objekt an, das endgültige Zugriff hat.  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 Maske, um die Zugriffsattribute von `DBG_ATTRIB_FLAGS`zu extrahieren.  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 Gibt an, dass kein angegebenen Speichertyp wird.  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 Gibt globalen Speicher an.  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 Gibt statischen Speicher an.  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 Gibt Speicherplatz im Register an.  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 Maske, um die Speicherung von Attributen aus `DBG_ATTRIB_FLAGS`zu extrahieren.  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 Gibt an, dass kein Typ modifizierer vorhanden ist.  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 Gibt an, dass der Typ von Objekt virtuell ist.  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 Gibt an, dass der Typ des Objekts ist konstant.  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 Gibt an, dass der Typ des Objekts synchronisiert wird.  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 Gibt an, dass der Typ des Objekts flüchtig ist.  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 Maske, um die Typattribute von `DBG_ATTRIB_FLAGS`zu extrahieren.  
  
 DBG\_ATTRIB\_DATA  
 Gibt an, dass dieses Objekt ein Datenfeld ist.  
  
 DBG\_ATTRIB\_METHOD  
 Gibt an, dass dieses Objekt eine Methode ist.  
  
 DBG\_ATTRIB\_PROPERTY  
 Gibt an, dass dieses Objekt eine Eigenschaft darstellt.  
  
 DBG\_ATTRIB\_CLASS  
 Gibt an, dass es sich bei dem Objekt um eine Klasse handelt.  
  
 DBG\_ATTRIB\_BASECLASS  
 Gibt an, dass dieses Objekt eine Basisklasse ist.  
  
 DBG\_ATTRIB\_INTERFACE  
 Gibt an, dass dieses Objekt eine Schnittstelle ist.  
  
 DBG\_ATTRIB\_INNERCLASS  
 Gibt an, dass dieses Objekt eine innere Klasse ist.  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 Gibt an, dass dieses Objekt „höchst\-*abgeleitet*“ ist.  Der Ausdruck“*höchst\-abgeleitete*„bedeutet den tatsächlichen Typ des Objekts und nicht den Typ des Verweises.  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 Gibt eine Maske von `DBG_ATTRIB_DATA` von `DBG_ATTRIB_MOSTDERIVED`an.  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 Gibt an, dass das Objekt die mehrere benutzerdefinierten Viewer zugeordnet sind.  
  
## Hinweise  
  
> [!NOTE]
>  Die Werte in dieser Enumeration werden nicht in der Assembly für C\# definiert.  Stattdessen müssen Sie die Definitionen für die Quelldatei kopieren.  
  
 Diese Flags werden auch verwendet, um untergeordnete Elemente eines Objekts zu filtern, z. B. wenn sie als Argument in [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)übergeben werden.  Die Werte können mit bitweisen `OR`kombiniert werden.  
  
 Das `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\-Flag ist ein Hinweis auf [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle aus der [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle abzurufen und [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) für eine Liste von benutzerdefinierten Viewern aufzurufen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)