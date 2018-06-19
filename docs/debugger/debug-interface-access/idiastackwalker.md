---
title: IDiaStackWalker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0f9c4509e56949d739af3e39e04b89f289edfbe
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465329"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Enthält Methoden, führen Sie einen Stapel zu durchlaufen, anhand der Informationen in der PDB-Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaStackWalker`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Ruft ab einen Stack-Frame-Enumerator für X86 Plattformen.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Ruft eine Stack-Frame-Enumerator für eine bestimmte Plattform-Typ ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird verwendet, um eine Liste der Stapelrahmen für einem geladenen Modul zu erhalten. Jede der Methoden übergeben ein [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) Objekt (von der Clientanwendung implementiert) die notwendigen Informationen, um die Liste der Stapelrahmen erstellen bereitstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird durch den Aufruf abgerufen der `CoCreateInstance` Methode mit der Klassenbezeichner `CLSID_DiaStackWalker` und die Schnittstellen-ID des `IID_IDiaStackWalker`. Im Beispiel wird gezeigt, wie diese Schnittstelle abgerufen wird.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie zum Abrufen der `IDiaStackWalker` Schnittstelle.  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)