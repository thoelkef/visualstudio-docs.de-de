---
title: IDiaStackWalkFrame | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150140"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwaltet den Stapel Kontext zwischen Aufrufen der [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) -Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaStackWalkFrame` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Ruft den Wert eines Register ab.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Legt den Wert eines Register fest.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Liest Speicher aus dem Image.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Durchsucht den angegebenen Stapel Rahmen nach der nächstgelegenen Rückgabeadresse der Funktion.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Adresse.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird während der Ausführung des Programms zum Lesen und Schreiben von Registern sowie zum Zugreifen auf den Speicher und zum Suchen von Rückgabe Adressen verwendet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Client Anwendung implementiert diese Schnittstelle und übergibt eine Instanz der Schnittstelle an die [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) -Methode. Dieselbe Instanz dieser Schnittstelle wird erneut und erneut verwendet, um den Status der Register bei jedem Aufruf der `execute` Methode beizubehalten. Die- `execute` Methode verwendet diese Schnittstelle auch, um die Rückgabeadresse zu bestimmen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
