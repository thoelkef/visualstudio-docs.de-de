---
title: GETNAME_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GETNAME_TYPE
helpviewer_keywords: GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb73d39aec7f364ce27ab06ef426d1c4a622878a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getnametype"></a>GETNAME_TYPE
Gibt den Namenstyp der Dateien abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Member  
 GN_NAME  
 Gibt einen Anzeigenamen des Dokuments oder der Kontext.  
  
 GN_FILENAME  
 Gibt den vollständigen Pfad des Dokuments oder der Kontext.  
  
 GN_BASENAME  
 Gibt einen Basisdateinamen statt einen vollständigen Pfad des Dokuments oder der Kontext.  
  
 GN_MONIKERNAME  
 Gibt einen eindeutigen Namen des Dokuments oder der Kontext in Form eines Monikers an.  
  
 GN_URL  
 Gibt einen URL-Namen des Dokuments oder der Kontext.  
  
 GN_TITLE  
 Gibt einen Titel des Dokuments an, falls vorhanden.  
  
 GN_STARTPAGEURL  
 Ruft die URL der beginnend für Prozesse ab.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden als Parameter übergeben der [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), und [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) Methoden an, welche Art von Namen zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)