---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c91ac932692ac63cfd4f8129fdff65993cddf2e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856107"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `riid`  
 [in] Die GUID der Schnittstelle abrufen.  
  
 `ppvObject`  
 [out] Gibt das Objekt, das die gewünschte Schnittstelle implementieren. [C++] diese direkt in den Typ für die gewünschte Schnittstelle umgewandelt werden kann. [C#] verwenden Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> Methode, um die gewünschte Schnittstelle abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, wenn die Debug-Engine, in ausgeführt wird der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Prozessbereich und die zu debuggende Programm wird im eigenen Prozessbereich ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)