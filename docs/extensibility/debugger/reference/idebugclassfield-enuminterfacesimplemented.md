---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords: IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c173077fea398dfcb8bd510650b61062bba2627
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der implementierten Schnittstellen darstellt. Gibt einen null-Wert zurück, wenn keine Schnittstellen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurück oder gibt "S_FALSE" zurück, wenn es keine von dieser Klasse implementierten Schnittstellen sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das eine Schnittstelle beschreibt. Beachten Sie, die nicht verwaltete [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code verwendet keine Schnittstellen als diskrete Entität, damit diese Methode immer einen null-Wert gibt bei nicht verwalteten [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)