---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250fa60ec1564b87ccc561400e8b378619e9e850
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930920"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest die angegebene Anzahl von Bytes beginnend beim angegebenen Offset aus einer ausführbaren Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
 "pcbdata"  
 [out] Gibt die Anzahl der gelesenen Bytes.  
  
 Daten]  
 [in, out] Ein Array, das sich aus der Datei gelesenen Bytes gefüllt wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der Code für die Unterstützung von DIA Datenbytes aus einer ausführbaren Datei, die über einen Offset absolute Datei laden aufgerufen. Diese Methode wird aufgerufen, Unterstützung des der [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



