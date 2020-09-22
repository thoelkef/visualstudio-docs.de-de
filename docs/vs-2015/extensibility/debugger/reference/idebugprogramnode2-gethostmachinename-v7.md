---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e4f1a3621dde3fba5e8a2dabf45eaceb5d8ea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841072"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Veraltet. Verwenden Sie nicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrHostMachineName`  
 vorgenommen Gibt den Namen des Computers zurück, auf dem das Programm ausgeführt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine-Implementierung sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!WARNING]
> Ab [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] wird diese Methode nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
