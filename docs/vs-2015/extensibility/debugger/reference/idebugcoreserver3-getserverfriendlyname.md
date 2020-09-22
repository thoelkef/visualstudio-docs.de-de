---
title: 'IDebugCoreServer3:: getserverfriendlyname | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa81daf7ab1d592e6a2cd460268e5d66925f61e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840915"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft einen anzeigen Amen für den Server ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 vorgenommen Gibt einen anzeigen Amen für den Server zurück.  
  
> [!NOTE]
> Der Aufrufer ist für das Freigeben der Zeichenfolge verantwortlich.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Für vom Benutzer gestartete Server ist der Name, der von dieser Methode zurückgegeben wird, der vollständige Name des Servers. Für automatisch gestartete Server ist der Name der Name des Computers, auf dem der Server ausgeführt wird.  
  
 Wenn Sie einen Computer orientierten Namen haben, müssen Sie die [getServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) -Methode aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
