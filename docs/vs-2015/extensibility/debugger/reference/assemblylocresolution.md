---
title: ASSEMBLYLOCRESOLUTION | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c088b27e686d42d800a6470fbbced8192c100bfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153603"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, in denen eine Assembly befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
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
