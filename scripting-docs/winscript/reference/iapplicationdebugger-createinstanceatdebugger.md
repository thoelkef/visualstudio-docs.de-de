---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft-Dokumentation
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
ms.openlocfilehash: 95489464128e706e755432bee991c5481f5af8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425829"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Ermöglicht die Erstellung von Objekten im Debuggerprozess von Code, Out-of-Process an den Debugger.  
  
> [!IMPORTANT]
> Diese Methode sollte nicht implementiert werden, da es sich um nicht vertrauenswürdigem Code zum Erstellen von beliebiger Objekten in einen vertrauenswürdigen debugthread ermöglicht.  
  
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
  
 Die Methode wird derzeit nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)