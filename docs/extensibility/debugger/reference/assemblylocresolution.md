---
title: ASSEMBLYLOCRESOLUTION | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03d05cf8c224a24d143feb3d22df4357d623d308
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933208"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Gibt an, in denen eine Assembly befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## <a name="members"></a>Member  
 ALR_NAME  
 Assembly befindet sich im aktuellen Namespace.  
  
 ALR_USERDIR  
 Assembly befindet sich in einem Benutzerverzeichnis.  
  
 ALR_SHAREDDIR  
 Assembly befindet sich in freigegebenen Verzeichnis.  
  
 ALR_REMOTEDIR  
 Assembly befindet sich in einem Remoteverzeichnis.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden zurückgegeben, durch die [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) und [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) Methoden.  
  
 Diese Werte können kombiniert werden, mit der `OR` Vorgang.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)