---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft-Dokumentation
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
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d90a0406d5325ee11ec5c6230110128abc14de5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893363"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `riid`  
 [in] Die GUID der Schnittstelle abrufen.  
  
 `ppvObject`  
 [out] Gibt das Objekt, das die gewünschte Schnittstelle implementieren. [C++] diese direkt in den Typ für die gewünschte Schnittstelle umgewandelt werden kann. [C#] verwenden der <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um die gewünschte Schnittstelle abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, wenn die Debug-Engine, in ausgeführt wird der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Prozessbereich und die zu debuggende Programm wird im eigenen Prozessbereich ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)

