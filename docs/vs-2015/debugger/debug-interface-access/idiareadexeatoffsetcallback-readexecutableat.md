---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ac5452437ab6fdec3eb68baf46aeeab8434df4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538862"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest die angegebene Anzahl von Bytes ab dem angegebenen Offset aus einer ausführbaren Datei.  
  
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
 in Der Offset in der ausführbaren Datei, ab dem gelesen werden soll.  
  
 cbData  
 in Anzahl der zu lesenden Bytes.  
  
 pcbData  
 vorgenommen Gibt die Anzahl der gelesenen Bytes zurück.  
  
 data[]  
 [in, out] Ein Array, das mit aus der Datei gelesenen Bytes gefüllt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird vom Dia-Unterstützungs Code aufgerufen, um Daten Bytes aus einer ausführbaren Datei mithilfe eines absoluten Dateioffsets zu laden. Diese Methode wird zur Unterstützung der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
