---
title: GetAutoInsertExtensions-Methode
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611177"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions-Methode
  Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.

 Diese Methode ist für eine spätere Verwendung vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*psaExtensionNames*|Die Erweiterungsnamen der apps für Office.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Hinweise
 Jede app für Office, eingefügt werden soll, wird als Office-Erweiterung Anwendungsname, der einen Wert unter entspricht zurückgegeben **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Der Host muss diese Werte in der Registrierung nachschlagen, und fügen Sie dann die Erweiterungen automatisch.
