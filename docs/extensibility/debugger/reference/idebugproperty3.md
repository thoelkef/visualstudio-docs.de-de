---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "IDebugProperty3-Schnittstelle"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle unterstützt:  
  
-   Eine willkürlich lange Zeichenfolge der Eigenschaft zugeordneten abrufen.  
  
-   Eine eindeutige ID mit der Standardzuordnung einer Eigenschaft.  
  
-   Eine Liste der benutzerdefinierten Viewern für die Eigenschaft abrufen.  
  
-   Ruft den Wert einer Eigenschaft mit der Fähigkeit festlegen, alle resultierenden Fehler zu melden  
  
## Syntax  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, um Unterstützung für lange Zeichenfolgen, Eigenschaften\-ID und benutzerdefinierten Viewer zu unterstützen.  
  
## Hinweise für Aufrufer  
 Aufruf [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProperty2`\-Schnittstelle zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den von `IDebugProperty2` geerbten Methoden macht die `IDebugProperty3`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Gibt die Länge der Zeichenfolge zurück, die der Eigenschaft zugeordnet ist.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Gibt die Zeichenfolge in einem vom Benutzer angegebenen Puffer zurück.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Erstellt eine eindeutige ID für diese Eigenschaft.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Zerstört die eindeutige ID für diese Eigenschaft.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Gibt die Anzahl von benutzerdefinierten Viewern zurück, dass diese angezeigt werden kann.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Gibt die Liste der benutzerdefinierten Viewern zurück, dass diese angezeigt werden kann.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Legt den Wert der Eigenschaft fest und gibt eine Fehlermeldung zurück, wenn alle schief wurde.|  
  
## Hinweise  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ist die bevorzugte Methode für den Debug\- Manager der Sitzung \(SDM\) einen Wert der Eigenschaft festzulegen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)