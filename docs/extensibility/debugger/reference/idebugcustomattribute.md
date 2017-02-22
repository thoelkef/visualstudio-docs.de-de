---
title: "IDebugCustomAttribute | Microsoft Docs"
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
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "IDebugCustomAttribute-Schnittstelle"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein benutzerdefiniertes Attribut dar und kann den Namen, das übergeordnete Element und den Klassentyp des Attributs angeben.  
  
## Syntax  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Symbol für diese Schnittstelle implementiert, um den benutzerdefinierten Attributen zu unterstützen, die mit einem Symbol zugeordnet sind.  Es wird in der Regel in einem eigenen Objekt implementiert.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [Weiter](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) gibt diese Schnittstelle zurück.  Ein Aufruf der [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)\-Methode gibt die [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)\-Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugCustomAttribute`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ruft das Rechteck ab, auf den das aktuelle Attribut angefügt wird.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ruft den Typ des benutzerdefinierten Attributklassen ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ruft den Namen des benutzerdefinierten Attributs ab.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ruft die attributierten Informationen als BLOB von Bytes ab.|  
  
## Hinweise  
 Ein benutzerdefiniertes Attribut ist eine Struktur für C\#, das benutzerdefinierte Metadaten von Zubehör mit einer bestimmten Klasse oder eine Methode zugeordnet haben.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)