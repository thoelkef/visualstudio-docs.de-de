---
title: 'Idebuggenericfielddefinition:: constructinstantiierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57a28cfd3b2ccd2ff37fae80d426817b664972fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180899"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt eine Feld Instanz, wenn ein Array von Typargumenten angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cArgs`  
 in Anzahl der Argumente im `ppArgs` Array.  
  
 `ppArgs`  
 in Ein Array, das die Typargumente enthält. Die Typargumente müssen geschlossene Typen sein (nicht generische oder vollständig instanziierte Generika).  
  
 `ppConstructedField`  
 vorgenommen Gibt die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle zurück, die das neue Feld darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Einschränkungen werden nicht geprüft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
