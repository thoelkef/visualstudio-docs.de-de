---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3a637608c8da5d7c5c5e0d857520a08ffae494a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944865"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Liest die angegebene Anzahl von Bytes beginnend beim angegebenen Offset aus einer ausführbaren Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 fileOffset  
 [in] Der Offset in die ausführbare Datei gelesen werden soll.  
  
 cbData  
 [in] Die Anzahl der zu lesenden Bytes.  
  
 pcbData  
 [out] Gibt die Anzahl der gelesenen Bytes.  
  
 data[]  
 [in, out] Ein Array, das sich aus der Datei gelesenen Bytes gefüllt wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der Code für die Unterstützung von DIA Datenbytes aus einer ausführbaren Datei, die über einen Offset absolute Datei laden aufgerufen. Diese Methode wird aufgerufen, Unterstützung des der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)