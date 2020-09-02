---
title: IDiaStackWalker | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f5f5c3fa70c022175208cee492f3c0e752826e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144681"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt Methoden bereit, mit denen ein Stapel Durchlauf mithilfe von Informationen in der PDB-Datei durchgeführt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaStackWalker` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Ruft einen Stapel Rahmen Enumerator für x86-Plattformen ab.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Ruft einen Stapel Rahmen Enumerator für einen bestimmten Plattformtyp ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird verwendet, um eine Liste der Stapel Rahmen für ein geladenes Modul zu erhalten. Jeder Methode wird ein [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) -Objekt, das von der Client Anwendung implementiert wird, übermittelt, das die erforderlichen Informationen zum Erstellen der Liste der Stapel Rahmen bereitstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird durch den Aufruf der `CoCreateInstance` -Methode mit dem Klassen Bezeichner `CLSID_DiaStackWalker` und der-Schnittstellen-ID abgerufen `IID_IDiaStackWalker` . Das Beispiel zeigt, wie diese Schnittstelle abgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie die- `IDiaStackWalker` Schnittstelle abrufen.  
  
```cpp#  
  
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
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
