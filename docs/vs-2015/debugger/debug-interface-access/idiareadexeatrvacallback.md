---
title: IDiaReadExeAtRVACallback | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75bdd6e2e8c5ee8144b68253fa691792a267a5d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523723"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaReadExeAtRVACallback](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiareadexeatrvacallback).  
  
Ermöglicht eine Clientanwendung Bytes einer ausführbaren Datei gemäß der eine relative virtuelle Adresse angeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaReadExeAtRVACallback`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Liest die angegebene Anzahl von Bytes, beginnend ab der angegebenen relativen virtuellen Adresse (RVA) der ausführbaren Datei an.|  
  
## <a name="remarks"></a>Hinweise  
 Die Client-Anwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mit der eine relative virtuelle Adresse in der ausführbaren Datei Datei bereitzustellen. Um eine absolute Dateioffset verwenden zu können, implementieren die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Methode implementiert, die von der Clientanwendung und übergeben die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode als eine alternative Methode zum Lesen der Datei.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)



