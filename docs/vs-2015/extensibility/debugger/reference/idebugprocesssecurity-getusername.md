---
title: IDebugProcessSecurity::GetUserName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe52eb2f90d6d957132d56313f1636d058e1bd0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200654"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Benutzernamen aus den Anschlusslieferanten ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [out] Eine Zeichenfolge mit den Benutzernamen ein.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Andernfalls wird einen Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 `GetUserName` Gibt den Benutzernamen zurück, die in angezeigt wird der **Benutzernamen** Spalte die **an den Prozess anhängen** Dialogfeld. Anzeigen der **an den Prozess anhängen** Dialogfeld klicken Sie auf **an den Prozess anhängen** auf die **Tools** im Menü der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

