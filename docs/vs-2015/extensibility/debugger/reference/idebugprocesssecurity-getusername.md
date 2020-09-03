---
title: 'Idebugprocesssecurity:: GetUserName | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202783"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Benutzernamen vom Port Lieferanten ab.  
  
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
 vorgenommen Eine Zeichenfolge, die den Benutzernamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 `GetUserName` Gibt den Benutzernamen zurück, der in der Spalte **Benutzername** im Dialogfeld **an den Prozess anhängen** angezeigt wird. Um das Dialogfeld **an den Prozess anhängen** anzuzeigen, klicken Sie **im Menü Extras in der** integrierten Entwicklungsumgebung (IDE) auf **an den Prozess anhängen** [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
