---
title: GETNAME_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40ee5cb4bf552b04683c4c2119a8c43a595b2105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900305"
---
# <a name="getnametype"></a>GETNAME_TYPE
Gibt den Namenstyp von Dateien, die abgerufen werden.  
  
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
 Gibt einen Anzeigenamen des Dokuments oder der Kontext an.  
  
 GN_FILENAME  
 Gibt den vollständigen Pfad des Dokuments oder der Kontext an.  
  
 GN_BASENAME  
 Gibt einen Basisdateinamen anstelle eines vollständigen Pfads des Dokuments oder der Kontext an.  
  
 GN_MONIKERNAME  
 Gibt einen eindeutigen Namen des Dokuments oder der Kontext in Form eines Monikers an.  
  
 GN_URL  
 Gibt einen URL-Namen des Dokuments oder der Kontext.  
  
 GN_TITLE  
 Gibt einen Titel des Dokuments an, falls vorhanden.  
  
 GN_STARTPAGEURL  
 Ruft die URL der ab für Prozesse an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden übergeben, als Parameter an die [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), und [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) Methoden, um welche Art von Namen zurückzugebenden angeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)