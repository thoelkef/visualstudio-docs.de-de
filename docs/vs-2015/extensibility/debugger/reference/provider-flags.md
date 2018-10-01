---
title: PROVIDER_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a37c758a588576a823bd7d5abd685ce7f14b488
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523660"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [PROVIDER_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/provider-flags).  
  
Gibt die gewünschte Eigenschaften von einem Programm-Anbieter abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
typedef DWORD PROVIDER_FLAGS;  
```  
  
```csharp  
public enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
```  
  
## <a name="members"></a>Member  
 PFLAG_NONE  
 Keine Flags angegeben.  
  
 PFLAG_REMOTE_PORT  
 Eine Liste der Programme auf einem anderen Computer als "Aufrufer" [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 PFLAG_DEBUGGEE  
 Der Prozess wird von dieser Instanz der gerade gedebuggten [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 PFLAG_ATTACH_TODEBUGGEE  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] das derzeit debuggte Programm angefügt ist, jedoch wurde nicht gestartet.  
  
 PFLAG_REASON_WATCH  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] wird für Ereignisse überwachen.  
  
 PFLAG_GET_PROGRAM_NODES  
 Aufrufer möchte, dass die `ProgramNodes` Feld der [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur.  
  
 PFLAG_GET_IS_DEBUGGER_PRESENT  
 Aufrufer möchte, dass die `fIsTheDebuggerPresent` Feld der `PROVIDER_PROCESS_DATA` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden an die folgenden Methoden übergeben:  
  
-   [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
-   [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
-   [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

