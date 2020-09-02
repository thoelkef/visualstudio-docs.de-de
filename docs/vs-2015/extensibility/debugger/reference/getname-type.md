---
title: GETNAME_TYPE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160140"
---
# <a name="getname_type"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Namen der abzurufenden Dateien an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_GETNAME_TYPE {   
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
public enum enum_GETNAME_TYPE {   
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
 Gibt einen anzeigen Amen für das Dokument oder den Kontext an.  
  
 GN_FILENAME  
 Gibt den vollständigen Pfad des Dokuments oder des Kontexts an.  
  
 GN_BASENAME  
 Gibt einen Basis Dateinamen anstelle eines vollständigen Pfads des Dokuments oder des Kontexts an.  
  
 GN_MONIKERNAME  
 Gibt einen eindeutigen Namen für das Dokument oder den Kontext in Form eines Monikers an.  
  
 GN_URL  
 Gibt einen URL-Namen des Dokuments oder des Kontexts an.  
  
 GN_TITLE  
 Gibt einen Titel des Dokuments an, sofern vorhanden.  
  
 GN_STARTPAGEURL  
 Ruft die URL der Startseite für Prozesse ab.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden als Parameter an die Methoden [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)und [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) übermittelt, um anzugeben, welche Art von Name zurückgegeben werden soll.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
