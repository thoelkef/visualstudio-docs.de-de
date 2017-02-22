---
title: "BPERESI_FIELDS | Microsoft Docs"
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
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "BPERESI_FIELDS-enumeration"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die über eine fehlgeschlagene Auflösung eines Haltepunkts Informationen abgerufen werden sollen.  
  
## Syntax  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Mitglieder  
 PERESI\_BPRESLOCATION  
 Initialisieren Sie das Feld\/verwenden, `bpResLocation` \(Haltepunkt auflösungs\) der Speicherort [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur.  
  
 BPERESI\_PROGRAM  
 Initialisieren Sie `pProgram` \/verwenden das Feld `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI\_THREAD  
 Initialisieren Sie `pThread` \/verwenden das Feld `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI\_MESSAGE  
 Initialisieren Sie `bstrMessage` \/verwenden das Feld `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI\_TYPE  
 Initialisieren Sie das Feld\/verwenden, `dwType`\-Typ der Haltepunkt \(\), der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI\_ALLFIELDS  
 Initialisieren Sie `BP_ERROR_RESOLUTION_INFO` \/verwenden alle Felder der Struktur.  
  
## Hinweise  
 Übergabe als Parameter an die [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)\-Methode, um anzugeben, welche Felder der [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur initialisiert werden sollen.  
  
 Diese Werte werden auch verwendet, um anzugeben, welche Felder in der `BP_ERROR_RESOLUTION_INFO` Struktur verwendet und gültig sind, wenn diese Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)