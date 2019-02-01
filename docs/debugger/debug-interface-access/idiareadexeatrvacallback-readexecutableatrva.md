---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a075369a9064425bd0cffe096dbe96ca30b402
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999105"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Liest die angegebene Anzahl von Bytes, beginnend ab der angegebenen relativen virtuellen Adresse (RVA) der ausführbaren Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `relativeVirtualAddress`  
 [in] Die RVA in der ausführbaren Datei gelesen werden soll.  
  
 `cbData`  
 [in] Die Anzahl der zu lesenden Bytes.  
  
 `pcbData`  
 [out] Gibt die Anzahl der gelesenen Bytes.  
  
 `data[]`  
 [in, out] Ein Array, das sich aus der Datei gelesenen Bytes gefüllt wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der Code für die Unterstützung von DIA Datenbytes aus einer ausführbaren Datei, die mit der eine relative virtuelle Adresse Laden aufgerufen. Diese Methode wird aufgerufen, Unterstützung des der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)