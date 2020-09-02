---
title: 'Idebugsymbolprovider:: GetLanguage | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8124e0c6328695da9773edbfd949ec2634dbfdb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421771"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft die Sprache ab, die zum Kompilieren des Codes an der debugadresse verwendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 in Ein Adress Objekt, das durch eine [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird.  
  
 `pguidLanguage`  
 vorgenommen Gibt einen zurück `GUID` , der die Sprache angibt.  
  
 `pguidLanguageVendor`  
 vorgenommen Gibt einen zurück `GUID` , der den Anbieter der Sprache angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Debug-Engine ruft diese Methode auf, um die Informationen zu erhalten, die Sie benötigen, um die richtige Ausdrucks Auswertung auszuwählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
