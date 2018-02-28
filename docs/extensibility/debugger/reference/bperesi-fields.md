---
title: BPERESI_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 36ac591940acaed2ac8b8f92c701580d9d45f94a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Gibt die Informationen über eine fehlgeschlagene Auflösung eines Haltepunkts abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 PERESI_BPRESLOCATION  
 Initialisieren/verwenden die `bpResLocation` (breakpointposition Auflösung) Feld der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur.  
  
 BPERESI_PROGRAM  
 Die Initialisierung/verwenden die `pProgram` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_THREAD  
 Die Initialisierung/verwenden die `pThread` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_MESSAGE  
 Die Initialisierung/verwenden die `bstrMessage` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_TYPE  
 Initialisieren/verwenden die `dwType` (Haltepunkt Type)-Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_ALLFIELDS  
 Alle Felder des initialisieren/verwenden die `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) Methode, um anzugeben, welche Felder von der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur initialisiert werden, sind.  
  
 Diese Werte werden auch verwendet, um anzugeben, welche Felder in der `BP_ERROR_RESOLUTION_INFO` Struktur verwendet und gültig sind, wenn dieser Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)