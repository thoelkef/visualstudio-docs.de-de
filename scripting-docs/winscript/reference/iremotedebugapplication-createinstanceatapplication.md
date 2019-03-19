---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft-Dokumentation
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
ms.openlocfilehash: 6e17c5abcb21bfaad6de948c3676d29232da66cf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146291"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Ermöglicht die Erstellung von Objekten in der der Anwendungsprozess von Code, Out-of-Process an die Anwendung.  
  
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
 [in] Klassen Sie-ID (CLSID) des zu erstellenden Objekts.  
  
 `pUnkOuter`  
 [in] Wenn `NULL`, das Objekt ist nicht als Teil eines Aggregats erstellt wird. Andernfalls `pUnkOuter` ist ein Zeiger auf des aggregatobjekts `IUnknown` Schnittstelle (das steuernde `IUnknown`).  
  
 `dwClsContext`  
 [in] Kontext für die Ausführung von ausführbarem Code. Die Werte stammen aus der Enumeration `CLSCTX`.  
  
 `riid`  
 [in] Der Schnittstellenbezeichner verwendet, um die Kommunikation mit dem Objekt.  
  
 `ppvObject`  
 [out] Adresse der Zeigervariable, die im angeforderten Schnittstellenzeiger empfängt `riid`. Nach der erfolgreichen Rückgabe *`ppvObject` enthält den angeforderten Schnittstellenzeiger. Bei einem Fehler \* `ppvObject` enthält `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode delegiert zur `CoCreateInstance`.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)