---
title: 'Ieedatastorage:: GetData | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a58f644a71601b16317c4fe63271f4f816da77d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149298"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die angegebene Anzahl von Bytes aus dem-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dataSize`  
 in Die Anzahl der abzurufenden bytes (das `data` Array muss mindestens diese Anzahl von Bytes enthalten).  
  
 `sizeGotten`  
 vorgenommen Gibt die Anzahl der tatsächlich abgerufenen Bytes zurück.  
  
 `data`  
 [in, out] Das Array, das mit den angeforderten Daten aufgefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die empfohlene Verwendung dieser Methode besteht darin, alle Daten Bytes in ein lokales Array abzurufen, da es keine Möglichkeit gibt, die Bytes im Abruf Vorgang zu überspringen. In diesem Fall sollte der-Parameter `dataSize` der Wert sein, der von der [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) -Methode zurückgegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
