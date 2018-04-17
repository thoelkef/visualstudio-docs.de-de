---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94fcc74943deb33e7f98ba24e9d7389a9d5746fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ruft den Benutzernamen des Lieferanten Port ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrUserName`  
 [out] Eine Zeichenfolge, die den Benutzernamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 `GetUserName` Gibt den Benutzernamen zurück, die in angezeigt wird der **Benutzername** Spalte die **an den Prozess anhängen** (Dialogfeld). Anzeigen der **an den Prozess anhängen** (Dialogfeld), klicken Sie auf **an den Prozess anhängen** auf die **Tools** im Menü der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)