---
title: 'IDebugStackFrame2:: getphysicalstackrange | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99fc1e635691fa290d0a8e4506ef55d677e9ff78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547649"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Computer abhängige Darstellung des Bereichs physischer Adressen ab, der einem Stapel Rahmen zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `paddrMin`  
 vorgenommen Gibt die niedrigste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.  
  
 `paddrMax`  
 vorgenommen Gibt die höchste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die von dieser Methode zurückgegebenen Informationen werden vom Sitzungs-Debug-Manager (SDM) zum Sortieren von Stapel Rahmen verwendet.  
  
 Es wird davon ausgegangen, dass die aufrufsstapel nach unten wächst, d. h., dass neue Stapel Rahmen bei immer niedrigeren Speicheradressen hinzugefügt werden. Eine Lauf Zeit Architektur muss physische Stapel Bereiche bereitstellen, die dieser Annahme entsprechen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
