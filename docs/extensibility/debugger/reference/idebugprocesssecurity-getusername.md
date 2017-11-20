---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 909c4b4e47bdc9de60b9761974843b370c7400e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
 `GetUserName`Gibt den Benutzernamen zurück, die in angezeigt wird der **Benutzername** Spalte die **an den Prozess anhängen** (Dialogfeld). Anzeigen der **an den Prozess anhängen** (Dialogfeld), klicken Sie auf **an den Prozess anhängen** auf die **Tools** im Menü der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)