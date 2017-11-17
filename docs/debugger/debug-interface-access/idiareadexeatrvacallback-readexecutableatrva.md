---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 907b75c6021a739ebbe52cbef1ec3e4714360072
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Liest die angegebene Anzahl von Bytes beginnend bei der angegebenen relativen virtuellen Adresse (RVA) aus der ausführbaren Datei.  
  
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
 [out] Gibt die Anzahl der gelesenen Bytes zurück.  
  
 `data[]`  
 [in, out] Ein Array, das sich aus der Datei gelesenen Bytes gefüllt ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der DIA Unterstützungscode Datenbytes aus einer ausführbaren Datei, die über eine relative virtuelle Adresse Laden aufgerufen. Diese Methode wird aufgerufen, unterstützen die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)