---
title: IDiaStackWalker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae33fc6c135322e6b6a0a965188848ddac363cbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993672"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Bietet Methoden, die Sie für einen Stapel durchlaufen, anhand der Informationen in die PDB-Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaStackWalker`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Ruft einen Stack-Frame-Enumerator für X86 Plattformen.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Ruft ein Stack-Frame-Enumerator für eine bestimmte Plattform-Typ ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird verwendet, um eine Liste der Stapelrahmen für ein geladenes Modul zu erhalten. Jede der Methoden übergeben einen [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) Objekt (von der Clientanwendung implementiert) bietet die erforderlichen Informationen zum Erstellen der Liste der Stapelrahmen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird abrufen durch Aufrufen der `CoCreateInstance` Methode mit dem Klassenbezeichner `CLSID_DiaStackWalker` und die Schnittstellen-ID des `IID_IDiaStackWalker`. Im Beispiel wird gezeigt, wie diese Schnittstelle abgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie erhalten die `IDiaStackWalker` Schnittstelle.  
  
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
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)