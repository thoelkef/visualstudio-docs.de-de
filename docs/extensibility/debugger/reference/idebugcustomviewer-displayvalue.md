---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732451"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Diese Methode wird aufgerufen, um den angegebenen Wert anzuzeigen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parameter
`hwnd`\
[in] Übergeordnetes Fenster

`dwID`\
[in] ID für benutzerdefinierte Viewer, die mehr als einen Typ unterstützen.

`pHostServices`\
[in]: Reserviert Immer auf null gesetzt.

`pDebugProperty`\
[in] Schnittstelle, die verwendet werden kann, um den anzuzeigenden Wert abzurufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Anzeige ist "modal", da diese Methode das erforderliche Fenster erstellt, den Wert anzeigt, auf Die Eingabe wartet und das Fenster schließt, bevor alles vor der Rückkehr zum Aufrufer. Dies bedeutet, dass die Methode alle Aspekte der Anzeige des Werts der Eigenschaft behandeln muss, vom Erstellen eines Fensters für die Ausgabe über das Warten auf Benutzereingaben bis hin zum Zerstören des Fensters.

 Um das Ändern des Werts für das angegebene [IDebugProperty3-Objekt](../../../extensibility/debugger/reference/idebugproperty3.md) zu unterstützen, können Sie die [SetValueAsStringWithError-Methode](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) verwenden, wenn der Wert als Zeichenfolge ausgedrückt werden kann. Andernfalls ist es erforderlich, eine benutzerdefinierte Schnittstelle – exklusiv für `DisplayValue` den Ausdrucksevaluator, `IDebugProperty3` der diese Methode implementiert – für dasselbe Objekt zu erstellen, das die Schnittstelle implementiert. Diese benutzerdefinierte Schnittstelle würde Methoden zum Ändern der Daten einer beliebigen Größe oder Komplexität bereitstellen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
