---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cb9ff60968d806cfdee0201746a02483895b0af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Liest die angegebene Anzahl von Bytes beginnend beim angegebenen Offset aus einer ausführbaren Datei.  
  
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
 [in] Der Offset in der ausführbaren Datei gelesen werden soll.  
  
 cbData  
 [in] Die Anzahl der zu lesenden Bytes.  
  
 pcbData  
 [out] Gibt die Anzahl der gelesenen Bytes zurück.  
  
 Daten]  
 [in, out] Ein Array, das sich aus der Datei gelesenen Bytes gefüllt ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der DIA Unterstützungscode Datenbytes aus einer ausführbaren Datei mit einem absoluten Dateioffset Laden aufgerufen. Diese Methode wird aufgerufen, unterstützen die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)