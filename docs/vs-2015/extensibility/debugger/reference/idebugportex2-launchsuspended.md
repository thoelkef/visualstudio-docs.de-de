---
title: IDebugPortEx2::LaunchSuspended | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d43d7e77efcb9cf507b6eab14e0f8fa4c757c92
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186538"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wird eine ausführbare Datei gestartet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```csharp  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszExe`  
 [in] Der Name des zu startenden ausführbaren Datei an. Dies kann sein, ein vollständiger Pfad oder relativ zum Arbeitsverzeichnis angegeben, der `pszDir` Parameter.  
  
 `pszArgs`  
 [in] Die Argumente, die an die ausführbare Datei übergeben werden sollen. Möglicherweise ein null-Wert ab, wenn keine Argumente vorhanden sind.  
  
 `pszDir`  
 [in] Der Name des Arbeitsverzeichnisses durch die ausführbare Datei. Möglicherweise ein null-Wert ab, wenn kein Arbeitsverzeichnis erforderlich ist.  
  
 `bstrEnv`  
 [in] Umgebungsblock mit Null endende Zeichenfolgen, gefolgt von einer weiteren NULL-Terminator.  
  
 `hStdInput`  
 [in] Handle für einen anderen Eingabedatenstrom. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `hStdOutput`  
 [in] Handle für einen anderen Ausgabestream. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `hStdError`  
 [in] Handle für einen anderen Fehlerausgabestream. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `ppPortProcess`  
 [out] Gibt eine [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt, das den gestarteten Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sollte gestartet werden, den Prozess so, dass die It angehalten wird und der Code nicht ausgeführt. Die [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) aufgerufen, um den Vorgang fortzusetzen.  
  
 Ein Programm kann auch über ein Debug-Engine gestartet werden. Weitere Informationen finden Sie unter [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md)

