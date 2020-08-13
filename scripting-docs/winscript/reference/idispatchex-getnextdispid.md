---
title: 'IDispatchEx:: GetNextDispID | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144428"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Listet die Member des-Objekts auf.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parameter

`grfdex`\
Bestimmt, welche Gruppe von Elementen aufgelistet werden soll. Dies kann eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|Standardwert für "f"|Fordert an, dass das-Objekt die Standardelemente auflistet. Das-Objekt kann beliebige Element Elemente auflisten.|
|"f"|Fordert an, dass das-Objekt alle-Elemente auflistet. Das-Objekt kann beliebige Element Elemente auflisten.|

`id`\
Identifiziert den aktuellen Member. "GetNextDispID" Ruft das Element in der-Enumeration ab. Verwendet GetDispID oder einen vorherigen GetNextDispID-Befehl, um diesen Bezeichner abzurufen. Verwendet den DISPID_STARTENUM Wert zum Abrufen des ersten Bezeichners des ersten Elements.

`pid`\
Adresse einer DispID-Variablen, die den Bezeichner des nächsten Elements in der Enumeration empfängt.

Wenn ein Member durch oder gelöscht `DeleteMemberByName` wird `DeleteMemberByDispID` , `DISPID` muss der für gültig bleiben `GetNextDispID` .

## <a name="return-value"></a>Rückgabewert

Gibt einen der folgenden Werte zurück:

|Wert|Bedeutung|
|-|-|
|`S_OK`|Erfolg.|
|`S_FALSE`|Die Enumeration ist abgeschlossen.|

## <a name="example"></a>Beispiel

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Siehe auch

- [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)