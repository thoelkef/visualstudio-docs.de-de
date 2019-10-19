---
title: 'Iremotedebuapplication:: "Webanwendung" | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572309"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Ermöglicht die Erstellung von Objekten im Anwendungsprozess durch Code, der außerhalb des Prozesses der Anwendung ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateInstanceAtApplication(  
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
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)