---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187266"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest die angegebene Anzahl von Bytes ab der angegebenen relativen virtuellen Adresse (RVA) aus der ausführbaren Datei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `relativeVirtualAddress`  
 in Die RVA in der ausführbaren Datei, die gelesen werden soll.  
  
 `cbData`  
 in Anzahl der zu lesenden Bytes.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der gelesenen Bytes zurück.  
  
 `data[]`  
 [in, out] Ein Array, das mit aus der Datei gelesenen Bytes gefüllt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird vom Dia-Unterstützungs Code aufgerufen, um Daten Bytes aus einer ausführbaren Datei mit einer relativen virtuellen Adresse zu laden. Diese Methode wird zur Unterstützung der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
