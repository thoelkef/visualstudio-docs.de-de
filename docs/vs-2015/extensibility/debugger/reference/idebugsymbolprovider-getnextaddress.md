---
title: 'Idebugsymbolprovider:: getnextaddress | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1bf0798e0f49d9e7b2871c5601f966bc282b186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421449"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die debugadresse ab, die einer bestimmten debugadresse in einer Methode folgt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 in Die angegebene debugadresse.  
  
 `fStatementOnly`  
 in Wenn true, werden die debugadressen auf eine einzige Anweisung beschränkt.  
  
 `ppAddress`  
 vorgenommen Gibt die nächste debugadresse zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen zurück `HRESULT` , in der Regel S_OK.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
