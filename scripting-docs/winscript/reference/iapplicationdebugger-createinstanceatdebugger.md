---
title: 'Iapplicationdebugger:: kreateingestanceatdebugger | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577887"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Ermöglicht das Erstellen von Objekten im Debuggerprozess durch Code, der außerhalb des Prozesses für den Debugger verarbeitet wird.  
  
> [!IMPORTANT]
> Diese Methode sollte nicht implementiert werden, da Sie nicht vertrauenswürdigem Code ermöglicht, beliebige Objekte in einem vertrauenswürdigen Debugger-Thread zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rclsid`  
 in Klassen Bezeichner (CLSID) des zu erstellenden Objekts.  
  
 `pUnkOuter`  
 in Wenn `NULL`, wird das Objekt nicht als Teil eines Aggregats erstellt. Andernfalls ist `pUnkOuter` ein Zeiger auf die `IUnknown`-Schnittstelle des aggregierten Objekts (das steuernde `IUnknown`).  
  
 `dwClsContext`  
 in Kontext zum Ausführen von ausführbarem Code. Die Werte stammen aus der-Enumeration `CLSCTX`.  
  
 `riid`  
 in Der Schnittstellen Bezeichner, der zur Kommunikation mit dem-Objekt verwendet wird.  
  
 `ppvObject`  
 vorgenommen Die Adresse der Zeiger Variablen, die den in `riid` angeforderten Schnittstellen Zeiger empfängt. Bei erfolgreicher Rückgabe enthält * `ppvObject` den angeforderten Schnittstellen Zeiger. Bei einem Fehler enthält \* `ppvObject` `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode delegiert an `CoCreateInstance`.  
  
 Die-Methode ist zurzeit nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)