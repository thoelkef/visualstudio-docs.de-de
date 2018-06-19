---
title: IDiaStackWalkHelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dac563f99697a8e43b5f7db9831e075c0ed7087
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464965"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Erleichtert das Durchlaufen des Stapels mithilfe der Anwendung debuggen Programmdatenbankdatei (.pdb)-Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in VTable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaStackWalkHelper`:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Ruft den Wert eines Registers.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Legt den Wert eines Registers.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Liest einen Block von Daten aus der ausführbaren Image im Arbeitsspeicher.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Sucht den angegebenen Stapelrahmen für die nächste Funktion Absenderadresse an.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Sucht den angegebenen Stapelrahmen für eine Absenderadresse Beginn oder kurz vor dem angegebenen Stapeladresse an.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Ruft ab den Stapelrahmen, der die angegebene virtuelle Adresse enthält.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Ruft das Symbol, das die angegebene virtuelle Adresse enthält. **Hinweis:** Symbol muss den Typ haben `SymTagFunctionType` (ein Wert aus der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Gibt zurück, der PDATA-Datenblock, der angegebenen virtuellen Adresse zugeordnet.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Ruft die virtuelle Startadresse einer ausführbaren Datei, wenn eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird von der DIA-Code zum Abrufen von Informationen über die ausführbare Datei, um eine Liste der Stapelrahmen während der Ausführung des Programms erstellen aufgerufen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Eine Clientanwendung implementiert diese Schnittstelle zum Durchlaufen des Stapels während der Ausführung des Programms zu unterstützen. Eine Instanz dieser Schnittstelle wird zum Übergeben der [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) oder [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)