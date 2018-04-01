---
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0aa4a5e044dfc28302735e058c8863d4eb683670
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Erstellt einen Enumerator für statische lokale Variablen der Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppLocals`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der statischen "lokal" darstellt. Gibt einen null-Wert zurück, wenn keine statische lokale Variablen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn es keine statischen "lokal sind". Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das verschiedene Typen von statischen "lokal" darstellt. Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für jedes Objekt, um zu bestimmen, genau welche Art von statischen lokalen für das Objekt darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)